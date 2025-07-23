Berikut ini adalah versi `README.md` dalam Bahasa Indonesia yang **sudah siap ditempel langsung** ke proyek Anda:

````markdown
# flask-minimal

Proyek starter Flask minimal yang dirancang untuk membantu Anda dengan cepat mengatur aplikasi web yang bersih, sederhana, dan efisien. Semua kode berada dalam satu file (`app.py`) dengan struktur template dan aset statis dasar.

## Fitur

- Aplikasi Flask dalam satu file (`app.py`) untuk memaksimalkan produktivitas dan kesederhanaan.
- Struktur HTML dasar dengan styling dan JavaScript minimal.
- Pengaturan proyek yang sederhana dan intuitif tanpa kompleksitas yang berlebihan.
- Mudah dikustomisasi untuk pengembangan aplikasi web yang cepat.

## Persiapan

```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip -y
````

## Instalasi

1. **Clone repositori:**

```bash
git clone https://github.com/yourusername/flask-minimal.git
cd flask-minimal
```

2. **Buat virtual environment (disarankan):**

```bash
python3 -m venv venv
source venv/bin/activate
```

3. **Instal dependensi yang dibutuhkan:**

```bash
pip install -r requirements.txt
```

4. **Jalankan aplikasi:**

```bash
python app.py
```

Aplikasi Flask akan berjalan dan dapat diakses melalui browser di:
👉 [http://localhost:5000](http://localhost:5000)

## Menjalankan Otomatis Setelah Reboot

Agar aplikasi Flask otomatis berjalan setelah server Ubuntu direboot, Anda bisa menggunakan systemd:

### 1. Buat file service:

```bash
sudo nano /etc/systemd/system/flask-minimal.service
```

### 2. Tempelkan konfigurasi berikut (sesuaikan path dan user):

```ini
[Unit]
Description=Flask Minimal App
After=network.target

[Service]
User=ubuntu
WorkingDirectory=/home/ubuntu/flask-minimal
ExecStart=/home/ubuntu/flask-minimal/venv/bin/python /home/ubuntu/flask-minimal/app.py
Restart=always

[Install]
WantedBy=multi-user.target
```

> Gantilah `/home/ubuntu/flask-minimal` dengan direktori proyek Anda, dan `User=ubuntu` dengan nama user di server Anda.

### 3. Aktifkan dan jalankan servicenya:

```bash
sudo systemctl daemon-reexec
sudo systemctl daemon-reload
sudo systemctl enable flask-minimal
sudo systemctl start flask-minimal
```

Dengan ini, Anda tidak perlu lagi menjalankan langkah `source venv/bin/activate` dan `python app.py` setiap kali server direboot — aplikasi akan otomatis dijalankan oleh sistem.

## Kustomisasi

Anda dapat mengedit:

* Template HTML di `templates/index.html`
* CSS di `static/style.css`
* JavaScript di `static/script.js`
* Logika dan routing di `app.py`

## Lisensi

Proyek ini dilisensikan di bawah MIT License.

## Kontribusi

Silakan fork dan ajukan pull request jika Anda memiliki ide atau perbaikan. Untuk saran atau laporan masalah, silakan buka *issue* di repositori ini.

---

Proyek ini cocok untuk memulai aplikasi web atau prototipe kecil dengan cepat, ringan, dan efisien.

```

Jika Anda ingin, saya juga bisa bantu generate isi `flask-minimal.service` yang disesuaikan langsung berdasarkan username dan path Anda. Mau?
```
