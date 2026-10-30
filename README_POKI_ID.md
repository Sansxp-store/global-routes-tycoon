# Global Routes Tycoon — Web Build (Poki submission candidate)

Build browser dari game HTML5. Jalankan dengan local web server (bukan membuka file langsung) untuk pengujian. `index.html` memuat Poki SDK resmi dan memanggil `gameLoadingFinished`, `gameplayStart` pada input pertama, serta `gameplayStop` saat tab/game disembunyikan.

## Status

Ini adalah **submission candidate / prototype**, belum dinyatakan lolos Poki Inspector atau QA. Sebelum meminta review:

1. Uji desktop, tablet, dan ponsel; pastikan memenuhi canvas 16:9 Poki (640x360, 836x470, atau 1031x580) dan skala tanpa memotong UI.
2. Jalankan melalui https://inspector.poki.dev/ dan perbaiki semua error/warning SDK dan QA.
3. Pastikan perilaku gameplayStart/gameplayStop benar untuk semua keadaan UI; tambahkan commercialBreak hanya pada alur pause → lanjut bermain yang benar-benar ada.
4. Buat 3 screenshot gameplay asli serta thumbnail statis dan animasi sesuai panduan Poki.
5. Upload build melalui akun Poki for Developers. Rilis global hanya dapat dilakukan setelah tahapan tes dan persetujuan Poki.

Dokumentasi resmi:
- https://developers.poki.com/guide/adding-your-game
- https://developers.poki.com/guide/requirements-quality
- https://developers.poki.com/guide/sdk-html5
- https://developers.poki.com/guide/share

Game menyimpan progres via localStorage di dalam try/catch agar kegagalan storage tidak menghentikan game. Tidak ada aset font/library eksternal selain Poki SDK.
