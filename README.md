# Hallo AI — Website

Landing page statis (`index.html`) + satu serverless function opsional (`api/chat.js`) untuk demo chatbot AI.

```
hallo-ai-site/
├── index.html      halaman utama
├── api/chat.js     demo chatbot AI (Groq), opsional
├── vercel.json     pengaturan Vercel
├── .env.example    contoh environment variable
└── .gitignore
```

## 1. Deploy (tanpa AI dulu)

Cara termudah, lewat GitHub:

1. Buat repository baru di GitHub, unggah isi folder ini.
2. Buka vercel.com, klik **Add New → Project**, pilih repository tadi.
3. Biarkan pengaturan default, klik **Deploy**.

Atau lewat terminal:

```bash
npm i -g vercel
cd hallo-ai-site
vercel        # login, ikuti pertanyaannya
vercel --prod
```

Demo chatbot di halaman langsung berfungsi dengan jawaban skrip.

## 2. Aktifkan demo AI (opsional)

1. Buat API key di console.groq.com.
2. Di Vercel: **Project → Settings → Environment Variables**, tambahkan
   - `GROQ_API_KEY` = kunci kamu
   - `GROQ_MODEL` = nama model yang tersedia di akun Groq kamu (default: `llama-3.1-8b-instant`, cek daftar model terbaru di console Groq)
3. Di `index.html`, ubah `const USE_AI_DEMO = false;` menjadi `true`.
4. Deploy ulang (`git push` atau `vercel --prod`).

Bila API gagal atau belum aktif, demo otomatis kembali ke jawaban skrip.

Perlindungan yang sudah ada: kunci hanya di server, prompt sistem dipegang server, panjang pesan dan jumlah riwayat dibatasi, dan ada pembatas 20 permintaan per IP per 10 menit. Pembatas ini hanya pengaman sederhana. Pasang juga batas pemakaian di dashboard Groq supaya biaya tidak membengkak.

## 3. Domain sendiri

1. Beli domain (`.id` atau `.com`).
2. Vercel: **Project → Settings → Domains → Add**, ikuti petunjuk DNS.

## 4. Yang perlu diubah di `index.html`

- `WA_NUMBER` dan `IG_USER` (bagian script paling atas)
- Harga di bagian Harga (masih angka contoh)
- Data contoh di demo (menu, jam, lokasi) bila ingin disesuaikan
- Jika memakai AI, ubah juga info usaha di `api/chat.js` agar sama dengan data demo

## 5. Setelah tayang

- Tes tombol WhatsApp dari HP
- Buat Google Business Profile untuk Hallo AI di Medan
- Taruh link website di bio Instagram dan di pesan outreach
