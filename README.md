# flask-minimal

Proyek starter Flask minimal yang dirancang untuk membantu Anda dengan cepat membuat aplikasi web yang bersih, sederhana, dan efisien. Proyek ini dibuat ringan dan berfokus pada produktivitas, dengan seluruh kode berada dalam satu file (`app.py`), serta dilengkapi dengan template dasar dan aset statis.

## Fitur

- Aplikasi Flask dalam satu file (`app.py`) untuk memaksimalkan kesederhanaan dan produktivitas.
- Struktur template HTML dasar dengan styling dan JavaScript minimal.
- Pengaturan proyek yang sederhana dan intuitif, tanpa kompleksitas berlebihan.
- Mudah dikustomisasi untuk pengembangan aplikasi web secara cepat.

## Persiapan

```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip -y
````

## Instalasi

1. Clone repositori:

   ```bash
   git clone https://github.com/yourusername/flask-minimal.git
   cd flask-minimal
   ```

2. Buat virtual environment (disarankan):

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. Instal dependensi:

   ```bash
   pip install -r requirements.txt
   ```

4. Jalankan aplikasi:

   ```bash
   python app.py
   ```

Aplikasi Flask akan berjalan, dan Anda dapat mengaksesnya melalui browser di alamat:
[http://localhost:5000](http://localhost:5000)

## Menjalankan Otomatis Setelah Reboot

### Menjalankan Otomatis Menggunakan crontab

Agar aplikasi Flask dapat berjalan otomatis setiap kali server dinyalakan ulang (reboot), Anda bisa menggunakan cron `@reboot`.

### Langkah-langkah:

1. Buka crontab dengan perintah:

   ```bash
   crontab -e
   ```

2. Tambahkan baris berikut di bagian paling bawah (ganti path sesuai lokasi folder proyek Anda):

   ```bash
   @reboot /bin/bash -c 'cd /home/ubuntu/flask-minimal && source venv/bin/activate && python app.py'
   ```

   > Gantilah `/home/ubuntu/flask-minimal` dengan path direktori Anda, dan pastikan nama user serta struktur venv sesuai.

3. Simpan dan keluar dari editor.

Setelah ini, aplikasi Flask Anda akan otomatis dijalankan setiap kali server direboot, tanpa perlu mengetik ulang perintah aktivasi environment dan menjalankan `app.py` secara manual.


### Menjalankan Otomatis Menggunakan `systemd` (Opsional)

Alternatif lain selain `crontab` adalah menggunakan `systemd` untuk membuat service yang akan otomatis dijalankan saat booting.

#### 1. Buat file service

Jalankan:

```bash
sudo nano /etc/systemd/system/flask-minimal.service
```

Isi file-nya seperti ini (ganti path dengan path proyek kamu):

```ini
[Unit]
Description=Flask Minimal Web App
After=network.target

[Service]
User=ubuntu
WorkingDirectory=/home/ubuntu/flask-minimal
ExecStart=/home/ubuntu/flask-minimal/venv/bin/python /home/ubuntu/flask-minimal/app.py
Restart=always

[Install]
WantedBy=multi-user.target
```

> **Catatan**:
>
> * Ganti `ubuntu` pada `User=` dengan nama user kamu.
> * Pastikan path ke `python` dan `app.py` benar.

#### 2. Reload systemd & aktifkan service

```bash
sudo systemctl daemon-reexec
sudo systemctl daemon-reload
sudo systemctl enable flask-minimal
sudo systemctl start flask-minimal
```

#### 3. Cek status aplikasi

```bash
sudo systemctl status flask-minimal
```

#### 4. Melihat log output Flask

```bash
journalctl -u flask-minimal -f
```

Setelah langkah ini, setiap kali server dinyalakan ulang (`reboot`), Flask akan langsung jalan secara otomatis via `systemd`.

---

Kalau kamu mau, saya bisa gabungkan versi systemd ini langsung ke README final yang tadi. Mau?


## Penggunaan

Proyek ini siap digunakan sebagai fondasi untuk membangun aplikasi web. File `app.py` sudah berisi semua rute dan logika dasar Flask, sehingga mudah untuk dikembangkan dan disesuaikan. Anda dapat menambahkan lebih banyak template, rute, atau file statis sesuai kebutuhan.

## Kustomisasi

Anda dapat dengan mudah mengubah:

* Struktur HTML di `templates/index.html`
* Tampilan CSS di `static/style.css`
* Interaktivitas JavaScript di `static/script.js`

Silakan modifikasi file `app.py` untuk menambahkan rute atau logika tambahan sesuai kebutuhan Anda.

## Lisensi

Proyek ini dilisensikan di bawah MIT License.

## Kontribusi

Silakan fork repositori ini dan kirim pull request jika Anda memiliki perbaikan atau peningkatan. Jika ada saran atau ide, Anda juga dapat membuka *issue* untuk berdiskusi bersama.

Proyek ini dibuat dengan fokus pada kesederhanaan dan efisiensi, sangat cocok untuk memulai proyek aplikasi web atau prototipe kecil dengan cepat dan ringan.
