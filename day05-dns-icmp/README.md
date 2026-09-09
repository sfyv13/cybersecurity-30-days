# Day 5 — ICMP + DNS Fundamentals & DNS Enumeration

## Nə etdim
- `dig example.com` ilə A record sorğuladım (2 IP tapıldı — load balancing)
- `dig example.com MX` ilə email server məlumatını sorğuladım (Null MX tapıldı)
- `dig google.com MX` və `dig google.com TXT` ilə real domendə MX/TXT record-ları analiz etdim
- Wireshark ilə DNS Query/Response paketlərini izlədim, DNS-in UDP üzərində işlədiyini gördüm

## Tapıntılar
- `example.com`: 2 A record (104.20.23.154, 172.66.147.243), Null MX (email qəbul etmir)
- `google.com`: MX → smtp.google.com (öz infrastrukturu), 17 TXT record (SPF, Apple/Facebook/DocuSign/Cisco domain verification)

## Öyrəndiklərim
- ICMP status/xəta mesajları daşıyır, "ICMP disabled" özü də bir məlumatdır (firewall aşkarlanması)
- DNS TTL (cache müddəti) ilə IP TTL (hop sayı) fərqli anlayışlardır
- Zone transfer — düzgün konfiqurasiya olunmamış DNS server-də bütün subdomain siyahısını ifşa edə bilər
- MX/TXT record-lar şirkətin istifadə etdiyi 3-cü tərəf xidmətləri (Google Workspace və s.) ifşa edir — sosial mühəndislik üçün faydalı
- Passiv recon = hədəfə paket getmir (ictimai DNS sorğusu), aktiv recon = hədəfin öz serverinə birbaşa sorğu (zone transfer cəhdi)

## Fayllar
- `day5_dns_traffic.pcapng` — DNS Query/Response trafikinin capture faylı
