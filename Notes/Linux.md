# Checklist for linux server have performance problems

1. uptime ⟶ çalışma süresi
2. dmesg -T | tail ⟶ kernel hataları
3. vmstat 1 ⟶ zamana göre istatistik
4. mpstat -P ALL 1 ⟶ CPU dengesi
5. pidstat 1 ⟶ process kullanımı
6. iostat -xz 1 ⟶ disk I/O
7. free -m ⟶ bellek kullanımı
8. sar -n DEV 1 ⟶ network I/O
9. sar -n TCP,ETCP 1 ⟶ TCP istatistik
10. top ⟶ genel istatistik