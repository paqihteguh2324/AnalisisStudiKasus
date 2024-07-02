# AnalisisStudiKasus
## 1. User Service

### **Komponen**

**a.Core**

Entity:user

- idUser
- username
- email
- password
- description
- picture
- gender
- role

Repository

- UserRepository

**b. Application Layer**

registerUser
- username
- email
- password
- description
- picture
- gender

loginUser
- email
- password

getProfile
- email
- password

updateProfile
- username
- description
- picture
- gender

C.**Infrastructure Layer**

- Database Adapter: Implementasi dari `UserRepository`
- Web Adapter: REST API untuk registrasi dan manajemen profil pengguna (NestJS)

### Fungsi utama

- registerUser
Membuat akun untuk user baru
- loginUser
User dapat melakukan login dan dapat melakukan updateProfile
- getProfile
melihat profile user
- updateProfile
Merubah data user

## 2. Event Service

### komponen

**a.Core**

Entity : event

- idEvent
- namaEvent
- tiketTersedia
- tglEvent

Repository : eventRepository

**b. Application Layer**

role admin

- createEvent
Membuat event
- updateEvent
Memperbaharui event
- deleteEvent
Menghapus event

role user

- getEvent
melihat daftar event yang tersedia

**c. Infrastructure Layer**

- Database Adapter: Implementasi dari `EventRepository`
- Web Adapter: REST API untuk manajemen event (NestJS)
- Event Adapter: Publikasi event ke Kafka untuk pembuatan, perubahan, atau penghapusan event

## 3. Booking Service

### Komponen

**a.Core**

Entity:Booking

- idBooking(PK)
- idEvent(FK)
- idUser(FK)
- isCancel
- isExpired

Repository
bookingRepository

**b.Application Layer**

- createBooking
melakukan pemesanan tiket
- cancelBooking 
membatalkan pemesanan tiket

**c. infrastructure Layer**

- Database Adapter: Implementasi dari `BookingRepository`
- Web Adapter: REST API untuk pemesanan tiket (NestJS)
- Event Adapter: Publikasi event ke Kafka untuk pemesanan dan pembatalan tiket

## 4.Payment Service

### Komponen

**a.Core**

Entity:Payment 

- idPayment(PK)
- idBooking(FK)
- paymentStatus
- paymentMethod

Repository

- paymentRepository

b. Application Layer

- createPayment
memproses pembayaran dari user
- updatePaymentStatus
merubah status pembayaran

**c.Infrastructure Layer**

- **Database Adapter: Implementasi dari `PaymentRepository`**
- **Web Adapter: REST API untuk memproses pembayaran (Golang)**
- **Event Adapter: Publikasi event ke Kafka untuk status pembayaran**

Untuk arsitektur saga patern
![Alt text](https://github.com/paqihteguh2324/AnalisisStudiKasus/blob/main/img/hex.png?raw=true "Saga")

untuk arsitektur hexagon
![Alt text](Img\hex.png "Saga")
