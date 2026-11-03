# Pendataan Mahasiswa (C++)

Program konsol C++ untuk mendata mahasiswa. Jumlah data ditentukan saat program berjalan, lalu setiap mahasiswa dicatat dengan NIM, nama, program studi, dan alamat. Hasilnya ditampilkan sebagai tabel dan sebagai daftar per indeks array.

## Fitur

Program menyimpan data di empat array 1D dinamis (`nim`, `nama`, `prodi`, `alamat`) yang ukurannya mengikuti jumlah mahasiswa yang diinput. Indeks yang sama di keempat array menunjuk ke satu mahasiswa yang sama.

Input divalidasi supaya program tidak berhenti di tengah jalan:

- Jumlah mahasiswa harus angka bulat antara 1 dan 1000. Input kosong, huruf, spasi, atau angka lebih dari 4 digit ditolak dan ditanyakan ulang.
- NIM hanya boleh berisi angka 0-9. NIM disimpan sebagai `string` sehingga angka 0 di depan tidak hilang.
- Jika input terputus di tengah jalan (misalnya Ctrl+D di Linux/macOS atau Ctrl+Z di Windows), program keluar dengan kode 1 dan tidak masuk ke perulangan tanpa akhir.

Memori dinamis dibebaskan dengan `delete[]` saat program selesai normal.

## Persyaratan

Kompiler C++ yang mendukung C++11 atau lebih baru, misalnya `g++` atau `clang++`.

## Kompilasi dan menjalankan

```bash
g++ -std=c++11 -Wall -Wextra main.cpp -o pendataan
./pendataan
```

Di Windows (MinGW), jalankan dengan `pendataan.exe`.

## Contoh sesi

Data di bawah hanya contoh.

```text
jumlah mahasiswa yang ingin didata (1-1000): 2

=== INPUT DATA MAHASISWA ===

Data Mahasiswa ke-1 (Indeks [0]):
NIM    : 2607441001
Nama   : Budi Santoso
Prodi  : Rekayasa Keamanan Siber
Alamat : Jakarta Selatan

Data Mahasiswa ke-2 (Indeks [1]):
NIM    : 2607441002
Nama   : Siti Aminah
Prodi  : Teknik Informatika
Alamat : Depok
```

Keluaran program:

```text
                            HASIL PENDATAAN MAHASISWA
=================================================================================
No  NIM           Nama                    Prodi                       Alamat
---------------------------------------------------------------------------------
1   2607441001    Budi Santoso            Rekayasa Keamanan Siber     Jakarta Selatan
2   2607441002    Siti Aminah             Teknik Informatika          Depok
=================================================================================

=== OUTPUT PEMANGGILAN LANGSUNG PER INDEKS ===
Indeks [0] -> 2607441001 | Budi Santoso | Rekayasa Keamanan Siber | Jakarta Selatan
Indeks [1] -> 2607441002 | Siti Aminah | Teknik Informatika | Depok
```

## Batasan

- Lebar kolom tabel tetap: nama 24 karakter, prodi 28 karakter. Teks yang lebih panjang tidak dipotong, sehingga kolom di sebelahnya akan bergeser.
- Nama, prodi, dan alamat boleh dikosongkan. Hanya jumlah dan NIM yang divalidasi.
- NIM tidak dicek duplikat.
- Data hanya hidup selama program berjalan. Tidak ada penyimpanan ke file.

## Struktur repositori

```text
.
├── main.cpp
└── README.md
```

## Penulis

Rakha Firjatullah, Politeknik Negeri Jakarta, D4 Rekayasa Keamanan Siber.
