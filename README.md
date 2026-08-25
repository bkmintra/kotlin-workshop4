# Ktor Task Management API

โปรเจกต์นี้เป็น RESTful API สำหรับจัดการรายการงาน (Task Management) ที่สร้างขึ้นด้วยภาษา Kotlin และ Ktor Framework

## เทคโนโลยีที่ใช้

- **Kotlin**: ภาษาหลักในการพัฒนา
- **Ktor Framework**: ใช้สำหรับการสร้าง Web Application (ใช้ Netty Engine)
- **kotlinx.serialization**: จัดการการแปลงข้อมูล (Serialization/Deserialization) ในรูปแบบ JSON
- **In-Memory Repository**: เก็บข้อมูลการทำงานชั่วคราวไว้ในหน่วยความจำ (List)

## โครงสร้างข้อมูล (Data Models)

- `Task(id: Int, content: String, isDone: Boolean = false)`
- `TaskRequest(content: String, isDone: Boolean = false)`

## API Endpoints

| HTTP Method | Endpoint      | รายละเอียด                                 | ผลลัพธ์ที่สำเร็จ (Status) | กรณีผิดพลาด (Status) |
| ----------- | ------------- | ------------------------------------------ | ------------------------- | -------------------- |
| `GET`       | `/tasks`      | ดึงข้อมูล Task ทั้งหมด                     | `200 OK`                  | -                    |
| `GET`       | `/tasks/{id}` | ดึงข้อมูล Task ตาม ID ที่ระบุ              | `200 OK`                  | `404 Not Found`      |
| `POST`      | `/tasks`      | สร้าง Task ใหม่ โดยรับ Request Body เข้ามา | `201 Created`             | -                    |
| `PUT`       | `/tasks/{id}` | แก้ไข/อัปเดต Task ตาม ID                   | `200 OK`                  | `404 Not Found`      |
| `DELETE`    | `/tasks/{id}` | ลบข้อมูล Task ตาม ID                       | `204 No Content`          | `404 Not Found`      |

## การรันโปรเจกต์

รันคำสั่งเหล่านี้ผ่าน Terminal หรือ Command Line ในโฟลเดอร์โปรเจกต์:

- **รันเซิร์ฟเวอร์ API:**
  ```bash
  ./gradlew run
  ```
- **รันการทดสอบ (Unit Tests):**
  ```bash
  ./gradlew test
  ```
- **บิวด์โปรเจกต์:**
  ```bash
  ./gradlew build
  ```

หลังจากเซิร์ฟเวอร์รันสำเร็จ จะแสดงข้อความประมาณนี้:

```
2024-12-04 14:32:45.584 [main] INFO  Application - Application started in 0.303 seconds.
2024-12-04 14:32:45.682 [main] INFO  Application - Responding at http://0.0.0.0:8080
```

จากนั้นคุณสามารถเรียกใช้งาน API ผ่าน `http://localhost:8080` (เช่นด้วย Postman, cURL หรือ Browser) ได้เลย
