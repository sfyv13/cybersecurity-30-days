# Day 02 — TCP/UDP Handshake

## 🎯 Məqsəd
Bu günün məqsədi TCP three-way handshake prosesini, əlaqənin necə qurulduğunu, 
RST paketləri ilə əlaqənin necə kəsildiyini və tam bir TCP sessiyasının 
Wireshark vasitəsilə trafik təhlilini öyrənmək idi.

## 🛠️ İstifadə olunan alətlər
- Wireshark
- Kali Linux (VMware)

## 📂 Fayllar

| Fayl | Təsvir |
|------|--------|
| `DAY2.pcapng` | Standart TCP three-way handshake (SYN → SYN-ACK → ACK) trafikinin capture edilməsi |
| `DAY2_RST.pcapng` | Əlaqənin RST paketi ilə qəfil kəsilməsi (connection reset) trafiki |
| `DAY2_TCP_session_traffic.pcapng` | Tam bir TCP sessiyası boyu ötürülən paketlərin ardıcıllığı |

## 🔍 Öyrənilənlər
- **TCP Three-Way Handshake**: SYN, SYN-ACK, ACK mərhələləri necə işləyir
- **RST paketi**: əlaqənin normal bağlanması (FIN) ilə qəfil kəsilməsi (RST) arasındakı fərq
- **Sequence/Acknowledgment nömrələri**: TCP-nin etibarlı çatdırılmanı necə təmin etdiyi
- **Wireshark filtrləri**: `tcp.flags.syn==1`, `tcp.flags.reset==1` kimi filtrlərdən istifadə

## 📸 Screenshot-lar
Yuxarıdakı `.pcapng` faylları Wireshark-da açılaraq baxıla bilər.

## ➡️ Növbəti addım
Day 03 — daha dərin protokol analizi və/və ya UDP trafik müqayisəsi.
