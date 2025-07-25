# Üz Tanıma ilə Ödəniş Sistemi

## 📌 Layihə Haqqında
Bu sistem istifadəçilərə üzlərini kameraya göstərməklə, fiziki karta və ya mobil tətbiqə ehtiyac olmadan ödəniş etməyə imkan verir. Qeydiyyat və ödəniş zamanı biometrik identifikasiya tətbiq olunur.

## 🎯 Məqsəd
- Təhlükəsiz və sürətli ödəniş prosesi təmin etmək
- Fiziki kart və mobil cihazlara ehtiyacı aradan qaldırmaq
- Biometrik identifikasiya ilə müasir ödəniş modelini tətbiq etmək

## 🧩 Əsas Xüsusiyyətlər
- Üz tanıma ilə qeydiyyat və ödəniş
- “Sima” sistemi ilə üz identifikasiyasının yoxlanması
- Qeydiyyat zamanı canlılıq yoxlaması (liveness detection)
- Cihaz və ödəniş məntəqələrinin idarə edilməsi
- API ilə inteqrasiya

## 🛠️ Texnologiyalar və Komponentlər
- Backend: RESTful API (Node.js / Python / Java)
- Biometrik inteqrasiya: Sima (external verification)
- Məlumat bazası: PostgreSQL
- Mobil tətbiq: Android / iOS
- İnfrastruktur: Docker, Kubernetes (əgər tətbiq olunubsa)

## 📑 API Endpoint-lər
| Metod | URL                            | Açıqlama                      |
|-------|--------------------------------|-------------------------------|
| POST  | /api/face-registrations        | Üz tanıma ilə qeydiyyat       |
| PATCH | /api/face-registrations/{id}/deactivate | Qeydiyyatı deaktiv et   |
| DELETE| /api/face-registrations/{id}   | Üz profilini sil              |
| POST  | /api/face-payments             | Üz tanıma ilə ödəniş          |
| GET   | /api/face-payments/{id}        | Ödəniş detalları              |
| GET   | /api/face-payments/user/{user_id} | İstifadəçi üzrə ödənişlər  |
| GET   | /api/devices/{id}              | Cihaz detalları               |
| GET   | /api/payment-places            | Bütün ödəniş nöqtələri        |
| GET   | /api/payment-places/{id}       | Nöqtə detalları               |

## 🔐 Təhlükəsizlik
- Üz datası AES-256 ilə şifrələnir
- Token-based autentifikasiya (JWT)
- Canlılıq yoxlaması ilə saxta girişlərə qarşı qorunma
- İcazəsiz girişlərin loglanması və audit

## 📂 Məlumat Bazası Strukturu
Əsas cədvəllər:
- `face_registrations`
- `face_payments`
- `identification_devices`
- `payment_places`

## 🔄 İş Axını
1. İstifadəçi mobil tətbiqdə üzünü skan edir
2. Sistem Base64 formatında üz datasını `Sima`ya göndərir
3. Sima yoxlama nəticəsini qaytarır
4. Əgər uyğunluq varsa, istifadəçi qeydiyyatdan keçir
5. Sonra ödənişlər həyata keçirilə bilər
