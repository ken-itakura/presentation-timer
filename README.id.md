# Timer Presentasi

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [हिन्दी](README.hi.md) | [Español](README.es.md) | [Français](README.fr.md) | [العربية](README.ar.md) | [বাংলা](README.bn.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Bahasa Indonesia](README.id.md) | [Deutsch](README.de.md) | [한국어](README.ko.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md)

Timer satu halaman untuk perkenalan diri bergiliran di acara reuni dan sejenisnya. Cukup buka `index.html` di browser — tanpa instalasi, server, atau koneksi internet.

## Cara pakai

1. Buka `index.html` di browser (Safari / Chrome).
2. Di layar pengaturan: muat CSV (lihat `sample/participants.csv` atau “Muat contoh”), atur kehadiran tiap orang, urutkan berdasarkan kolom apa pun, tentukan judul / waktu per orang / sapaan / bahasa, lalu coba suaranya.
3. Tekan “Ke timer” (ini juga mengaktifkan suara).
4. Jalankan timer:

| Aksi | Efek |
|---|---|
| `Spasi` / tombol Mulai | Mulai pembicara berikutnya (dengan tepuk tangan) |
| Klik nama di daftar kanan | Mulai orang itu; yang sebelumnya pindah ke “Dilewati” |
| Klik nama di “Dilewati” | Mulai orang itu |
| Hapus centang “Hadir” di “Dilewati” | Setelah konfirmasi, ditandai tidak hadir dan dihapus dari daftar (timer tetap berjalan) |

Sisa 10 detik: tik tiap detik · sisa 3 detik: bip cepat · 0 detik: suara ledakan dan label “Waktu habis!”. Kanan atas menampilkan total waktu berlalu; kolom kanan menampilkan 10 pembicara berikutnya.

## Format CSV

Baris pertama adalah header. UTF-8 dan Shift_JIS dideteksi otomatis. Kolom nama dan sapaan dipilih otomatis dari header (mis. `nama`, `sapaan`) dan bisa diubah di pengaturan. Jika sel sapaan kosong, dipakai sapaan default.

```csv
name,honorific,group,year
Alex Morgan,,A,2001
Sam Rivera,Dr.,B,2001
```

## Bahasa

16 bahasa: ganti lewat “Bahasa” di layar pengaturan (awalnya memakai bahasa browser, pilihan Anda disimpan). Teks antarmuka, judul dan sapaan default, data contoh, serta posisi sapaan (sebelum/sesudah nama) mengikuti bahasa; bahasa Arab memakai tata letak kanan-ke-kiri. Terjemahan belum ditinjau penutur asli — sunting `I18N` di `index.html` untuk memperbaikinya. Untuk menambah bahasa, tambahkan entri di `LANGS`, `I18N`, dan `SAMPLE_NAMES`.

## Seluler

Tata letak untuk ponsel potret dan lanskap. Di iPhone, sakelar senyap mematikan suara. Membuka file lewat aplikasi Berkas paling andal; dengan GitHub Pages cukup buka URL.

## Struktur

```
.
├── index.html            # app (HTML / CSS / JavaScript in one file)
├── sample/
│   └── participants.csv  # sample list
├── README.md             # + README.<lang>.md (16 languages)
└── LICENSE               # MIT
```

`index.html` berisi semuanya: kamus bahasa, pengurai CSV, layar pengaturan, sintesis suara dengan Web Audio (tanpa file audio), logika timer (berbasis stempel waktu sehingga tidak melenceng), dan layar jalannya acara. Pengaturan dan progres tersimpan otomatis di `localStorage`.

Lisensi: [MIT](LICENSE)
