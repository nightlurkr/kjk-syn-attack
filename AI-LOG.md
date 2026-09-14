# Log Penggunaan AI

**Mata Kuliah:** Keamanan Jaringan Komputer (ET234302)
**Tugas:** Class Activity 02 — Simulasi & Deteksi TCP SYN Flood
**Nama:** Ryan Adya Purwanto — **NRP:** 5027231046 — **Kelas:** Paralel A
**Tanggal pengerjaan:** 13 September 2026

---

## 1. Alat AI yang Digunakan

| Alat | Peran |
|---|---|
| Claude (Anthropic) | Pendamping belajar: memandu langkah lab, menjelaskan teori, dan membantu menyusun laporan |

## 2. Pembagian Kerja

Untuk transparansi, berikut pemisahan tegas antara yang dikerjakan AI dan yang dikerjakan sendiri.

### Dikerjakan sendiri (oleh mahasiswa)

- Menjalankan seluruh perintah (`hping3`, `tcpdump`, Wireshark) di VM Kali Linux milik sendiri.
- **Seluruh data empiris berasal dari eksekusi ini**: kedua file capture (`baseline.pcapng`, `attack.pcap`) dan keenam screenshot adalah hasil tangkapan nyata dari lab pribadi, bukan buatan/rekaan AI.
- Menyiapkan lingkungan lab (VMware, jaringan, konektivitas antar-mesin).
- Memverifikasi setiap hasil di layar sebelum dilaporkan.

### Dibantu AI

- Menjelaskan konsep TCP three-way handshake dan cara kerja SYN Flood.
- Memandu langkah teknis lab secara bertahap (identifikasi IP, pemilihan target, troubleshooting).
- Memberi saran metode yang lebih aman saat VM sempat freeze.
- Membantu menafsirkan hasil Wireshark dan menyusun struktur serta redaksi laporan `README.md` berdasarkan data asli yang saya kumpulkan.

## 3. Kronologi Interaksi

| # | Yang saya minta / lakukan | Bantuan AI |
|---|---|---|
| 1 | Memahami tugas & memastikan cukup waktu | Membedah tugas menjadi rencana bertahap |
| 2 | Menentukan IP penyerang & korban | Mengoreksi target dari `192.168.177.2` (gateway NAT) ke `192.168.177.1` (Windows) |
| 3 | Ping ke korban gagal | Menjelaskan bahwa ICMP diblokir Windows Firewall — jalur TCP tetap hidup |
| 4 | Merekam trafik normal (baseline) | Memandu cara capture & verifikasi handshake sehat |
| 5 | Menjalankan serangan; VM freeze saat `--flood` | Mendiagnosis penyebab; mengganti ke perekaman `tcpdump` + laju terkendali `-i u200` |
| 6 | Serangan berhasil (5.000 paket) | Membaca keluaran hping3 & mengaitkannya ke gejala serangan |
| 7 | Mengumpulkan bukti di Wireshark | Menunjuk filter, Protocol Hierarchy, I/O Graph, Conversations yang perlu di-screenshot |
| 8 | Meminta laporan README | Menyusun `README.md` lengkap dari data yang saya kumpulkan |

## 4. Verifikasi & Pemahaman

Saya memahami setiap langkah dan hasil dalam laporan ini, termasuk:

- Alasan jumlah SYN-ACK nol (IP spoofing membuat balasan terkirim ke alamat palsu, bukan ke penyerang).
- Mengapa `--flood` membekukan VM dan mengapa `tcpdump` + laju terbatas lebih aman.
- Cara membedakan trafik normal dari serangan lewat rasio SYN : SYN-ACK dan pola I/O Graph.

## 5. Pernyataan Integritas

Penggunaan AI dalam tugas ini bersifat sebagai alat bantu belajar dan penyusunan laporan. Seluruh simulasi dijalankan sendiri pada lingkungan lab tertutup milik saya, dan seluruh bukti (capture serta screenshot) adalah hasil nyata eksekusi tersebut. Isi laporan telah saya baca, pahami, dan verifikasi kebenarannya.

**Ryan Adya Purwanto — 5027231046**
