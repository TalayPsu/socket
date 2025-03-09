ในส่วนของ code ผมได้เขียนหมดทั้ง 3 ตัว แต่จะเลือกอธิบายแค่ตัว thread เท่านั้น
ผมได้ใช้โปรแกรม คำนวณ Fibonacci ไว้ใน fib.py
โค้ดนี้เป็น Multi-threaded Fibonacci TCP Server ที่ทำงานโดย:

ใช้ socket(AF_INET, SOCK_STREAM) สร้าง TCP socket
ตั้งค่า SO_REUSEADDR ให้สามารถรีใช้พอร์ตเดิมได้
bind(address) ผูกเซิร์ฟเวอร์กับพอร์ต 25000
listen(5) รอรับการเชื่อมต่อจาก client

เมื่อมี client เชื่อมต่อ (sock.accept()), สร้าง Thread ใหม่เพื่อจัดการ client นั้น

อ่านค่าที่ client ส่งมา (client.recv(100))
คำนวณค่า Fibonacci (fib(int(req)))
ส่งค่ากลับไปยัง client
รองรับหลาย client พร้อมกัน

โดย Thread จะทำให้สามารถคำนวณ Fibonacci สำหรับหลาย client ได้พร้อมกัน
