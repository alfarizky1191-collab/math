# Math Fighter

Math Fighter adalah game latihan matematika kelas 1 berbasis HTML, CSS, dan JavaScript. Progress pemain disimpan di browser lewat `localStorage`, sedangkan leaderboard dan challenge online memakai Firebase Firestore jika tersedia.

## Fix yang sudah diterapkan

- Leaderboard memakai Anonymous Auth UID sebagai document id, jadi pemain dengan nama yang sama tidak saling menimpa skor.
- Challenge teman bisa disimpan ke Firestore saat online, dengan fallback lokal kalau Firebase/Auth belum aktif.
- Stage hanya clear kalau skor minimal `3/5`.
- Jawaban salah sekarang dihitung sebagai satu attempt, lalu jawaban benar ditampilkan.
- Achievement skor sempurna memakai `bestStageScore`, bukan total skor kumulatif.
- Mapping stage generator diselaraskan dengan label unit workbook.

## Firebase

Aktifkan **Anonymous Authentication** di Firebase Console agar penulisan leaderboard dan challenge online bekerja.

Deploy rules contoh:

```bash
firebase deploy --only firestore:rules
```

Rules contoh ada di `firestore.rules`. Rules ini membatasi bentuk data dan mencegah overwrite skor pemain lain, tetapi validasi skor penuh tetap idealnya dilakukan di backend/Cloud Function kalau game dipakai publik.
