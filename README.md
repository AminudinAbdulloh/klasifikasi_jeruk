# Klasifikasi Jeruk

Proyek ini berisi aplikasi machine learning sederhana untuk memprediksi kualitas jeruk berdasarkan karakteristik fisik dan informasi panen. Model dilatih dari dataset `jeruk_balance_500.csv`, disimpan sebagai file `model_klasifikasi_jeruk.joblib`, lalu digunakan oleh aplikasi Streamlit pada `app_streamlit.py`.

## Demo Aplikasi

Aplikasi sudah dideploy dan dapat diakses melalui link berikut:

https://ml-klasifikasi-jeruk.streamlit.app/

## Fitur

- Prediksi kualitas jeruk melalui antarmuka web Streamlit.
- Input data berupa diameter, berat, tebal kulit, kadar gula, asal daerah, warna, dan musim panen.
- Menampilkan label prediksi kualitas jeruk beserta tingkat keyakinan model.
- Notebook eksperimen tersedia untuk eksplorasi data, training model, evaluasi, dan export model.

## Struktur Proyek

```text
.
|-- app_streamlit.py                 # Aplikasi web Streamlit
|-- belajar_klasifikasi_jeruk.ipynb  # Notebook eksplorasi, training, dan evaluasi model
|-- jeruk_balance_500.csv            # Dataset klasifikasi jeruk
|-- model_klasifikasi_jeruk.joblib   # Model machine learning hasil training
|-- requirements.txt                 # Daftar dependensi Python
`-- README.md                        # Dokumentasi proyek
```

## Dataset

Dataset berisi 500 data jeruk dengan distribusi kelas yang relatif seimbang:

| Kualitas | Jumlah Data |
| --- | ---: |
| Bagus | 168 |
| Sedang | 166 |
| Jelek | 166 |

Kolom yang digunakan sebagai fitur:

| Kolom | Tipe | Keterangan |
| --- | --- | --- |
| `diameter` | Numerik | Diameter jeruk |
| `berat` | Numerik | Berat jeruk |
| `tebal_kulit` | Numerik | Ketebalan kulit jeruk |
| `kadar_gula` | Numerik | Kadar gula jeruk |
| `asal_daerah` | Kategorikal | Daerah asal jeruk |
| `warna` | Ordinal | Warna jeruk: hijau, kuning, oranye |
| `musim_panen` | Kategorikal | Musim panen: kemarau atau hujan |
| `kualitas` | Target | Label kualitas: Bagus, Sedang, atau Jelek |

## Alur Machine Learning

Notebook `belajar_klasifikasi_jeruk.ipynb` memuat alur utama berikut:

1. Membaca dataset dari `jeruk_balance_500.csv`.
2. Melakukan eksplorasi data dan visualisasi sederhana.
3. Memisahkan fitur (`X`) dan target (`y`).
4. Membagi data menjadi data latih dan data uji dengan `test_size=0.2` dan `random_state=42`.
5. Melakukan preprocessing:
   - `StandardScaler` untuk fitur numerik.
   - `OneHotEncoder` untuk fitur kategorikal `asal_daerah` dan `musim_panen`.
   - `OrdinalEncoder` untuk fitur `warna`.
6. Melatih model `LogisticRegression` menggunakan `Pipeline`.
7. Mengevaluasi model dengan accuracy, classification report, dan confusion matrix.
8. Menyimpan model ke `model_klasifikasi_jeruk.joblib`.

## Instalasi

Pastikan Python sudah terinstal. Disarankan menggunakan virtual environment.

```bash
python -m venv .venv
```

Aktifkan virtual environment:

```bash
# Windows PowerShell
.venv\Scripts\Activate.ps1
```

```bash
# Linux/macOS
source .venv/bin/activate
```

Install dependensi:

```bash
pip install -r requirements.txt
```

## Cara Menjalankan Aplikasi

Jalankan Streamlit dari folder proyek:

```bash
streamlit run app_streamlit.py
```

Setelah server berjalan, buka URL yang ditampilkan oleh Streamlit, biasanya:

```text
http://localhost:8501
```

## Cara Menggunakan

1. Atur nilai input menggunakan slider dan pilihan yang tersedia.
2. Klik tombol `Prediksi`.
3. Aplikasi akan menampilkan hasil prediksi kualitas jeruk dan persentase keyakinan model.

## File Penting

- `app_streamlit.py`: memuat antarmuka aplikasi, input pengguna, pemanggilan model, dan output prediksi.
- `belajar_klasifikasi_jeruk.ipynb`: memuat proses pembelajaran model dari dataset.
- `model_klasifikasi_jeruk.joblib`: model yang digunakan langsung oleh aplikasi Streamlit.
- `requirements.txt`: dependensi yang diperlukan, yaitu `pandas`, `matplotlib`, `seaborn`, `scikit-learn`, `joblib`, dan `streamlit`.

## Catatan

- Pastikan file `model_klasifikasi_jeruk.joblib` berada di folder yang sama dengan `app_streamlit.py` saat aplikasi dijalankan.
- Jika model ingin diperbarui, jalankan ulang notebook training lalu simpan kembali model dengan nama file yang sama.
- Rentang input pada aplikasi mengikuti konfigurasi slider di `app_streamlit.py`.

## Pembuat

Dibuat oleh Aminudin Abdulloh.
