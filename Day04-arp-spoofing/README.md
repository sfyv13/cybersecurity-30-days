# Day 4 — ARP və ARP Spoofing Anlayışı

## Nə etdim
- `arp -a` ilə Kali-nin ARP cache-inə baxdım
- `arp-scan --localnet` ilə şəbəkədəki canlı host-ları aktiv şəkildə skan etdim
- ARP cache-i sıfırlayıb (`ip neigh flush all`), yenidən ping edərək Wireshark-da tam ARP Request/Reply mübadiləsini izlədim

## Tapılan host-lar (arp-scan + arp -a nəticəsi)
| IP | MAC | Vendor | Qeyd |
|---|---|---|---|
| 192.168.0.1 | c0:c9:e3:7e:bc:8a | TpLinkTechno | Router/Gateway |
| 192.168.0.102 | 38:7a:0e:b7:aa:e3 | TpLinkTechno | Naməlum cihaz |
| 192.168.0.104 | 00:0c:29:c2:5e:2a | VMware | Kali (skan edən maşın) |
| 192.168.0.105 | 00:0c:29:ea:5f:ae | VMware | Metasploitable (hədəf) |

## ARP Request/Reply nümunəsi (Wireshark)
1. `Who has 192.168.0.105? Tell 192.168.0.104` — Broadcast (ARP Request)
2. `192.168.0.105 is at 00:0c:29:ea:5f:ae` — Unicast (ARP Reply)

## Öyrəndiklərim
- ARP, IP ünvanını MAC ünvanına çevirir, autentifikasiya mexanizmi yoxdur
- ARP Spoofing bu etibarı istismar edərək MITM (Man-in-the-Middle) hücumuna imkan verir
- Eyni IP-yə iki fərqli MAC cavabı — ya zərərsiz IP reassignment, ya da ARP Spoofing ola bilər
- Fərqi ayırd etmək: normal halda MAC-lər ardıcıl dəyişir (biri yox olur, digəri gəlir), spoofing zamanı ikisi eyni zaman kəsiyində, tez-tez (saniyələrlə) növbələşərək cavab verir

## Fayllar
- `day4_arp_traffic.pcapng` — ARP Request/Reply trafikinin capture faylı
