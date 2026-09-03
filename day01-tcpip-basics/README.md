# Day 1 — TCP/IP Hacker Perspektivi

## Nə etdim
- Kali Linux + Metasploitable2 VM-lərini qurdum, bridged network ilə eyni şəbəkəyə qoşdum
- ping və traceroute ilə host arasında bağlantını test etdim
- Wireshark ilə ICMP trafikini capture etdim, TTL dəyərini analiz etdim (TTL=64)

## Öyrəndiklərim
- OSI-nin hər layerinin "hücum səthi" kimi necə oxuna biləcəyini
- TTL-in nə olduğunu və router hop-larını necə göstərdiyini
- Wireshark-da filter istifadəsini (icmp)

## Fayllar
- `DAY1.pcapng` — Kali-Metasploitable arasında ping trafikinin capture faylı
