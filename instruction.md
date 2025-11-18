Berikut FLOW / ALUR SISTEM lengkap untuk project
⭐ Weather & Outfit Recommender (menggunakan OpenWeather API + Gemini)

🌤️ FLOW WEBSITE (Updated: OpenWeather Version)
1️⃣ User buka website

Halaman utama menampilkan:

Input kota (textbox)

Tombol “Cek Cuaca”

2️⃣ User mengetik kota (misal: “Jakarta”)

User klik Submit.

3️⃣ Front-end (React) memanggil OpenWeather API

📌 Endpoint:

https://api.openweathermap.org/data/2.5/weather?q=JAKARTA&units=metric&appid=API_KEY


📌 Request utama:

q → nama kota

units=metric → suhu °C

appid → API key

4️⃣ OpenWeather mengembalikan data cuaca

React menerima data seperti:

main.temp → suhu

main.humidity → kelembapan

weather[0].main → kondisi cuaca (Rain, Clouds, Clear)

wind.speed → kecepatan angin

Contoh:

{
  "main": {
    "temp": 30.5,
    "humidity": 70
  },
  "weather": [
    { "main": "Clouds", "description": "broken clouds" }
  ],
  "wind": { "speed": 3.6 }
}


UI menampilkan:

Suhu

Cuaca

Ikon cuaca

Info lainnya

5️⃣ React merangkum data cuaca → dikirim ke Gemini API

Prompt yang dikirim:

Buat rekomendasi outfit berdasarkan kondisi cuaca berikut:

Kota: Jakarta
Suhu: 30°C
Cuaca: Clouds (mendung)
Kelembapan: 70%
Angin: 3.6 m/s

Berikan:
1. Saran outfit
2. Barang yang harus dibawa

6️⃣ Gemini membalas dengan saran outfit

Contoh output:

Outfit yang disarankan:
- Kaos katun ringan
- Celana panjang nyaman
- Sepatu breathable

Barang yang perlu dibawa:
- Payung untuk jaga-jaga
- Botol minum

7️⃣ React menampilkan rekomendasi dari Gemini

Halaman menunjukkan:

⛅ Cuaca hari ini

Suhu

Cuaca

Ikon

Info tambahan

👕 Rekomendasi Outfit

(hasil dari Gemini)

🎒 Barang yang perlu dibawa

(hasil dari Gemini)

8️⃣ (Opsional) Fitur tambahan

Simpan kota favorit (localStorage)

Mode dark/light

Notifikasi “Hari ini berpotensi hujan”

Rekomendasi outfit pagi / malam


🎨 GAMBARAN FLOW DALAM SINGKAT:
User input kota
        ↓
React panggil OpenWeather API
        ↓
Terima data cuaca (suhu, hujan, angin)
        ↓
React kirim ringkasan data ke Gemini
        ↓
Gemini generate rekomendasi outfit
        ↓
React tampilkan hasil ke user