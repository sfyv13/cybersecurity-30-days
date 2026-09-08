# Day 3 — Ports & Services + Nmap Dərin Giriş

## Nə etdim
- Metasploitable-a qarşı SYN scan (-sS) işlətdim, 23 açıq port tapdım (default 1000 port aralığında)
- Seçdiyim idarəetmə interfeyslərinə (21,22,23,512,513,514,5900) version detection (-sV) etdim
- Tam port scan (-p-) + version detection işlətdim, 30 açıq port tapdım, nəticəni fayla yazdım (-oN)
- Wireshark ilə paralel capture edərək SYN scan-ın "stealth" adının niyə tam dəqiq olmadığını gördüm

## Tapılan 5 ən dəyərli açıq servis
| Port | Servis | Versiya | Qeyd |
|---|---|---|---|
| 21 | ftp | vsftpd 2.3.4 | Məlum backdoor (CVE-2011-2523) |
| 1524 | bindshell | Metasploitable root shell | Hazır backdoor, parolsuz root girişi |
| 23 | telnet | Linux telnetd | Şifrəsiz idarəetmə protokolu |
| 3632 | distccd | distccd v1 (GNU 4.2.4) | Məlum uzaqdan kod icra zəifliyi |
| 8180 | http | Apache Tomcat/Coyote JSP 1.1 | Default admin parolları riski |

## Öyrəndiklərim
- Port = servisin "qapısı", well-known portlar konvensiyadır, qanun deyil
- -sS = SYN göndər, RST ilə bağla (tam handshake tamamlamır)
- -sV = servisin dəqiq versiyasını öyrənmək üçün əlavə sorğular göndərir
- -p- = bütün 65535 portu yoxlamaq (default yalnız 1000 ən məşhuru yoxlanır)
- "Stealth" scan da Wireshark-da tam görünür — gizlilik yalnız server log-larında ola bilər

## Fayllar
- `day3_full_scan.txt` — tam port scan (-p- -sV) nəticəsi
