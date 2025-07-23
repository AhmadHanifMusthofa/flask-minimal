````markdown
# flask-minimal

Proyek starter Flask minimal untuk membuat aplikasi web ringan dan efisien menggunakan Python Flask. Semua kode berada di satu file (`app.py`) dengan struktur template dan aset statis dasar.

## Fitur

- Aplikasi Flask hanya dalam satu file
- Struktur HTML sederhana
- Instalasi cepat dan mudah
- Mudah dikembangkan untuk proyek kecil atau pembelajaran

## Persiapan

```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip -y
````

## Instalasi

```bash
git clone https://github.com/yourusername/flask-minimal.git
cd flask-minimal
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python app.py
```

Aplikasi dapat diakses melalui:
[http://localhost:5000](http://localhost:5000)

## Menjalankan Otomatis Saat Server Reboot

Buka crontab:

```bash
crontab -e
```

Tambahkan baris berikut (ubah direktori sesuai lokasi proyek):

```bash
@reboot /bin/bash -c 'cd /home/ubuntu/flask-minimal && source venv/bin/activate && python app.py'
```

## Kustomisasi

* Template HTML: `templates/index.html`
* CSS: `static/style.css`
* JavaScript: `static/script.js`
* Logic aplikasi: `app.py`

## Lisensi

MIT License

## Kontribusi

Fork dan ajukan pull request untuk pengembangan atau perbaikan.

```
```
