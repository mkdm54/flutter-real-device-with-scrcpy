# Solusi: Laptop Tidak Kuat Menjalankan Emulator Flutter

## Gunakan HP Android Sebagai Emulator dengan Scrcpy

Jika laptop kamu tidak cukup kuat untuk menjalankan emulator Flutter, kamu bisa menggunakan HP Android sebagai pengganti emulator. Caranya adalah dengan menampilkan dan mengontrol layar HP di laptop menggunakan **scrcpy**.

---

## Apa itu Scrcpy?

**Scrcpy** adalah tool open-source yang memungkinkan kamu menampilkan dan mengontrol perangkat Android melalui USB atau secara wireless dari PC.

---

## Langkah-langkah Instalasi Scrcpy

### 1. Unduh Scrcpy

- Kunjungi: [https://github.com/Genymobile/scrcpy/releases/tag/v3.2](https://github.com/Genymobile/scrcpy/releases/tag/v3.2)
- Scroll ke bawah, unduh file: `scrcpy-win64-v3.2.zip`

### 2. Ekstrak File

Ekstrak ke folder yang mudah diakses, misalnya:  
`C:\scrcpy`

### 3. Tambahkan ke PATH

- Buka _System Environment Variables_
- Pilih _Environment Variables_
- Di bagian _System variables_, pilih `Path` > `Edit` > `New`, lalu tambahkan path:  
  `C:\scrcpy`

### 4. Verifikasi Instalasi

Buka **Command Prompt**, lalu ketik:

```bash
scrcpy --version
```

Jika versi muncul, berarti instalasi berhasil.

---

## Persiapan HP Android

### 1. Aktifkan Developer Options

Masuk ke:  
**Pengaturan > Tentang Ponsel**, lalu ketuk **Build Number** sebanyak **7 kali**.

### 2. Aktifkan USB Debugging

Masuk ke:  
**Pengaturan > Opsi Pengembang**, lalu aktifkan **USB Debugging**.

---

## Cara Menjalankan Scrcpy [scrpy](/images/icon.ico)

### 1. Menggunakan Kabel USB (Paling Stabil)

- Sambungkan HP ke laptop menggunakan kabel USB
- Jalankan perintah berikut di **Command Prompt**:

```bash
scrcpy
```

Layar HP akan tampil dan bisa dikontrol dari laptop.

### 2. Menggunakan Wireless (Tanpa Kabel)

#### Langkah-langkah:

1. Sambungkan HP dan laptop ke jaringan **Wi-Fi** yang sama
2. Sambungkan HP ke laptop **sekali** menggunakan kabel USB untuk inisialisasi
3. Buka **Command Prompt**, lalu jalankan:
   ```bash
   adb tcpip 5555
   ```
4. Temukan alamat IP HP kamu (bisa dari  
   **Pengaturan > Tentang Ponsel > Status**)
5. Jalankan:
   ```bash
   adb connect [IP_ADDRESS]
   ```
   Contoh:
   ```bash
   adb connect 192.168.1.5
   ```
6. Setelah tersambung, **cabut kabel USB**
7. Jalankan:
   ```bash
   scrcpy
   ```

---

## Kesimpulan

Dengan kedua metode ini, kamu bisa menjalankan dan menguji aplikasi Flutter langsung di perangkat nyata **tanpa perlu emulator**, cocok untuk laptop dengan spesifikasi terbatas.

---

## Referensi

- [StackOverflow: How can I connect to Android with ADB over TCP?](https://stackoverflow.com/questions/2604727/how-can-i-connect-to-android-with-adb-over-tcp)
