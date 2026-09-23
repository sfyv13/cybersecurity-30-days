# Day 6 — DHCP, NAT, Routing — Pivoting-in Təməli

## Nə etdim
- `ip route`, `route -n`, `netstat -rn` ilə Kali-nin routing table-ına baxdım
- VMware-də Kali VM-inə ikinci network adapter (Host-only) əlavə etdim
- 2 adapter ilə routing table-ın necə dəyişdiyini müşahidə etdim
- "Dual-homed host" ssenarisini lab-da simulyasiya etdim

## Routing Table (1 adapter — əvvəl)
default via 192.168.0.1 dev eth0
192.168.0.0/24 dev eth0


## Routing Table (2 adapter — sonra)

default via 192.168.0.1 dev eth0
192.168.0.0/24 dev eth0
192.168.229.0/24 dev eth1 ← Gizli daxili şəbəkə!


## Şəbəkə Diaqramı

[Kali VM]
|
|--- eth0 (192.168.0.104) ----→ 192.168.0.0/24 (Bridged — ev şəbəkəsi)
| |
| 192.168.0.1 (Router/Gateway)
| |
| İnternet
|
|--- eth1 (192.168.229.128) --→ 192.168.229.0/24 (Host-only — gizli şəbəkə)


## Öyrəndiklərim
- NAT daxili IP-ləri xaricdən gizlədir — attacker üçün "kor nöqtə" yaradır
- Kompromis olunmuş hostun routing table-ı "hansı gizli şəbəkələr var?" sualına cavab verir
- "Dual-homed host" = iki şəbəkəyə bağlı host = pivoting üçün ən dəyərli hədəf
- Host-only şəbəkəsi = tam izolyasiya, yalnız pivoting vasitəsilə əlçatan
- Metric dəyəri kiçik olan interfeys daha prioritetlidir (eth0: 100, eth1: 101)

## Pivoting Ardıcıllığı (Mindset)
1. `ip route` → Gizli şəbəkələri tap
2. `ip a` → Neçə interfeys var?
3. Kompromis serverdən Nmap scan → Kim canlıdır?
4. Canlı hostlara `-sV` → Hansı servislər?
5. 
