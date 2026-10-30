# GLOBAL ROUTES TYCOON — Android

Proyek ini membungkus game HTML `Global Routes Tycoon` menjadi aplikasi Android native sederhana menggunakan Android WebView. File game disimpan di dalam APK/AAB, sehingga versi ini bisa dimainkan offline.

## Yang sudah disiapkan

- WebView Android dengan JavaScript dan DOM Storage aktif agar autosave `localStorage` bekerja.
- Package ID: `id.bulcreative.globalroutestycoon`.
- Nama aplikasi: `Global Routes Tycoon`.
- Target SDK 36 (Android 16), minimum SDK 23.
- Tidak meminta izin internet, lokasi, kontak, kamera, atau penyimpanan.
- Ikon aplikasi, ikon 512×512, dan feature graphic Play Store.
- Menu Kebijakan Privasi di dalam Pengaturan game.
- Draf `privacy-policy.html` untuk dipasang pada URL publik.

## Membuat APK untuk tes di HP

1. Instal Android Studio versi yang mendukung Android SDK 36.
2. Ekstrak folder proyek ini.
3. Buka Android Studio → **Open** → pilih folder `GlobalRoutesTycoon_Android`.
4. Saat diminta, instal Android SDK Platform 36 dan Build Tools yang direkomendasikan Android Studio.
5. Tunggu **Gradle Sync** selesai.
6. Pilih **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
7. APK debug akan berada di `app/build/outputs/apk/debug/app-debug.apk` (package debug memakai akhiran `.debug`).
8. Pindahkan APK ke HP Android, lalu instal untuk tes.

Alternatif command line setelah Gradle dan Android SDK terpasang: jalankan `gradle assembleDebug` dari folder proyek.

## Opsi build APK lewat GitHub Actions (tanpa memasang Android Studio di HP)

Folder `.github/workflows` sudah berisi workflow untuk membuat APK debug otomatis.

1. Buat repository GitHub baru, lalu upload seluruh isi folder proyek ini ke repository tersebut.
2. Buka tab **Actions** di repository GitHub.
3. Pilih workflow **Build Android Debug APK**, lalu tekan **Run workflow**.
4. Setelah proses selesai, buka hasil workflow dan unduh artifact `global-routes-tycoon-debug-apk`.
5. Ekstrak artifact, lalu instal APK di HP untuk pengujian.

Workflow ini hanya menghasilkan APK debug untuk tes. APK debug bukan file rilis Play Store. AAB release tetap perlu dibuat dan ditandatangani menggunakan kunci rilis milik developer.

## Membuat file AAB untuk Google Play

Google Play menggunakan **Android App Bundle (.aab)** untuk aplikasi baru. APK terutama dipakai untuk instalasi dan tes langsung.

1. Buka proyek di Android Studio dan pastikan game sudah diuji pada beberapa ukuran layar.
2. Pilih **Build → Generate Signed Bundle / APK**.
3. Pilih **Android App Bundle**.
4. Buat keystore release baru melalui wizard, atau pilih keystore milik sendiri.
5. Simpan file keystore dan password di tempat aman. Jangan kirim atau unggah keystore ke GitHub dan jangan menghapusnya. Keystore ini penting untuk update aplikasi di masa depan.
6. Pilih build variant `release`, lalu selesaikan proses build.
7. File AAB release akan muncul di `app/release/` atau lokasi output yang ditampilkan Android Studio.
8. Upload AAB tersebut ke jalur Internal testing di Google Play Console terlebih dahulu.

Jangan upload APK debug ke Play Store. Untuk Play Store gunakan AAB release yang sudah ditandatangani.

## Sebelum rilis — wajib dilengkapi

- Ganti `GANTI_EMAIL_KONTAK_SEBELUM_RILIS` di `privacy-policy.html` dengan email kontak developer yang aktif.
- Host `privacy-policy.html` di URL HTTPS yang bisa dibuka publik tanpa login. Contohnya GitHub Pages. Masukkan URL tersebut di Play Console dan sediakan juga aksesnya dari aplikasi.
- Pastikan nama developer dan detail kontak sesuai data akun Play Console.
- Buat screenshot aplikasi dari perangkat Android sungguhan untuk listing Play Store. Jangan gunakan mockup sebagai screenshot fitur aplikasi.
- Lengkapi Data safety, target audiens, rating konten, deklarasi iklan (versi ini tidak menampilkan iklan), email kontak, dan seluruh formulir App content di Play Console secara jujur.
- Uji autosave, reset progress, bonus harian, rotasi/perubahan ukuran layar, tombol Back, dan proses keluar-masuk aplikasi.

## Catatan identitas aplikasi

Package ID yang dipakai adalah `id.bulcreative.globalroutestycoon`. Tentukan dan finalkan ID ini sebelum membuat aplikasi di Play Console. Setelah aplikasi dipublikasikan, jangan mengganti package ID untuk update aplikasi yang sama.

## Catatan batasan build pada paket ini

Paket ini berisi **source project Android**, bukan APK/AAB hasil kompilasi. Lingkungan pembuatan file ini tidak menyediakan Android SDK, Android Build Tools, atau Gradle, sehingga binary APK/AAB tidak dapat dikompilasi dan diuji di sini. Android Studio akan mengunduh komponen build yang diperlukan saat proyek dibuka.
