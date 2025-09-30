# Network-Security-with-IDS-IPS

## 📌 Giới thiệu
Dự án này mô phỏng môi trường mạng an toàn với tường lửa **pfSense** và hệ thống phát hiện/ngăn chặn xâm nhập (**IDS/IPS** – ví dụ: Snort/Suricata).  
Mục tiêu nhằm nghiên cứu cách attacker có thể tấn công, và cách firewall + IDS/IPS giúp giám sát, cảnh báo hoặc ngăn chặn.

---

## 🖥️ Cấu trúc hệ thống
Mô hình gồm 3 máy ảo chính trong VirtualBox:

- **Attacker**: Máy giả lập kẻ tấn công (ví dụ: Kali Linux).  
- **pfSense**: Firewall trung gian, quản lý luồng dữ liệu và triển khai IDS/IPS.  
- **Victim**: Máy bị tấn công, chạy dịch vụ (VD: Web Server).  

Sơ đồ kết nối:
Attacker <----> pfSense <----> Victim

---

## ⚙️ Thiết lập môi trường
1. **Cài đặt VirtualBox** và tạo 3 VM: Attacker, pfSense, Victim.  
2. **Cấu hình card mạng**:  
   - Attacker ↔ pfSense (Internal Network 1)  
   - pfSense ↔ Victim (Internal Network 2)  
   - pfSense ↔ Host (NAT) để có Internet (tuỳ chọn).  
3. **Cấu hình pfSense**:  
   - Đặt địa chỉ IP cho WAN và LAN.  
   - Tạo rule cho phép ICMP để ping kiểm tra.  
   - Cài đặt Snort/Suricata làm IDS/IPS.  

---

## ✅ Kiểm tra kết nối
- Ping từ Attacker → Victim (qua pfSense).  
- Dùng pfSense logs để quan sát ICMP.  
- Thực hiện thử tấn công (VD: port scanning bằng nmap) để kiểm chứng IDS/IPS.  

---

## 📊 Kết quả đạt được
- Các máy ảo có thể giao tiếp thông qua pfSense.  
- IDS/IPS phát hiện được hoạt động quét cổng hoặc tấn công giả lập.  
- Hiểu rõ sự phối hợp giữa cấu hình mạng (VirtualBox), firewall (pfSense), và IDS/IPS.  

---

## 🔮 Hướng phát triển
- Bổ sung nhiều kịch bản tấn công hơn (SQLi, DoS/DDoS, brute-force).  
- Thử nghiệm Suricata thay cho Snort để so sánh hiệu năng.  
- Kết hợp thêm SIEM để thu thập và phân tích log tập trung.  

---

## 📚 Tài liệu tham khảo
- [pfSense Documentation](https://docs.netgate.com/pfsense/en/latest/)  
- [Snort Official](https://www.snort.org/)  
- [Suricata Official](https://suricata.io/)  
