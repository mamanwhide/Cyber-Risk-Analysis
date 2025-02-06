# Klasifikasi Jenis Serangan Siber Menggunakan Metode Certainty Factor dan Naive Bayes Classifier

##Deskripsi
Program ini dirancang untuk mengklasifikasikan jenis serangan siber berdasarkan dataset yang diberikan. Program menggunakan dua metode utama, yaitu **Naive Bayes Classifier (NBC)** dan **Certainty Factor (CF)**, untuk memprediksi jenis serangan. Hasil dari kedua metode kemudian dibandingkan berdasarkan akurasi yang didapatkan.

## Dataset
Dataset yang digunakan adalah `ai_ml_cybersecurity_dataset.csv`, yang berisi informasi tentang serangan siber, termasuk:
- `Event ID`: Identifikasi unik untuk setiap serangan.
- `Timestamp`: Waktu terjadinya serangan.
- `Source IP`: Alamat IP sumber serangan.
- `Destination IP`: Alamat IP tujuan serangan.
- `User Agent`: Informasi tentang perangkat atau browser yang digunakan.
- `Attack Type`: Jenis serangan (target yang akan diprediksi).
- `Attack Severity`: Tingkat keparahan serangan.
- `Data Exfiltrated`: Apakah data berhasil dicuri atau tidak.
- `Threat Intelligence`: Informasi intelijen tentang ancaman.
- `Response Action`: Tindakan yang diambil sebagai respons terhadap serangan.

## Metode yang Digunakan
### 1. Naive Bayes Classifier (NBC)
Naive Bayes adalah metode klasifikasi probabilistik yang mengasumsikan independensi antar fitur. Metode ini cocok untuk dataset dengan banyak fitur dan relatif mudah diimplementasikan.

### 2. Certainty Factor (CF)
Certainty Factor adalah metode yang digunakan untuk menangani ketidakpastian dalam sistem pakar. Metode ini menggunakan aturan-aturan yang ditentukan oleh pakar untuk menghitung tingkat keyakinan terhadap suatu hipotesis (jenis serangan).

## Cara Menjalankan Program
1. Pastikan dataset `ai_ml_cybersecurity_dataset.csv` berada di direktori yang sama dengan file `.ipynb`.
2. Jalankan program di Jupyter Notebook atau Google Colab.
3. Program akan melakukan preprocessing data, melatih model, dan mengevaluasi performa kedua metode.
4. Hasilnya akan ditampilkan dalam bentuk:
   - Confusion Matrix untuk Naive Bayes dan Certainty Factor.
   - Bar plot perbandingan akurasi kedua metode.
   - Laporan klasifikasi (precision, recall, F1-score) untuk setiap metode.

## Preprocessing Data
- Attack Type >> Target Klasifikasi
- User Agent, Threat Intelligence, Attac Severity >> Fitur Input 

## Pembagian Dataset
- Train 70%
- Test 30%
- Fitur (X):
    - Semua kolom kecuali Event ID, Timestamp, Source IP, Destination IP, Response Action & Attack Type
- Fitur (Y):
    - Attack Type (Label yang ingin diprediksi)

## Pembagian Library 
### Naive Bayes
- sklearn.naive_bayes.GaussianNB
- sklearn.model_selection.train_test_split
- sklearn.metrics.accuracy_score, classification_report, confusion_matrix
- matplotlib.pyplot & seaborn
### Certainty Factor (CF)
- numpy
- sklearn.preprocessing.LabelEncoder
- sklearn.metrics.accuracy_score
- classification_report, confusion_matrix

## Cara Kerja
### Naive Bayes Classifier (NBC)
- Menggunakan "GaussianNB()" dari sklearn.naive_bayes
- Mengasumsikan fitur dalam dataset
- Menggunakan "teorema Bayes" untuk menghitung probabilitas setiap kelas berdasarkan input fitur
- Memilih kelas dengan probabilitas tertinggi sebagai hasil prediksi
### Certainty Factor (CF)
- Aturan yang digunakan
    """
    Jenis Serangan (Attack Type)	User Agent	    Threat Intelligence	Attack Severity
    Ransomware	                    Windows (1)	    High (2)	        Critical (3)
    Malware	                        Linux (2)	    Medium (1)	        High (2)
    Phishing	                    Mobile (3)	    Low (0)	            Medium (1)
    DDoS Attack	                    IoT Device (4)	High (2)	        Critical (3)
    SQL Injection	                Web Browser (5)	Medium (1)	        High (2)
    """
- Perhitungan CF:
    - Jika fitur sesuai aturan >> CF * 0.8 (Tinggi)
    - Jika fitur tidak sesuai  >> CF * 0.2 (Rendah
    - Jika nilai CF tertinggi untuk suatu serangan, maka kategori tersebut dipilih sebagai hasil prediksi

## Hasil dan Perbandingan
### Akurasi
- **Naive Bayes Classifier**: Akurasi yang didapatkan adalah `20.42%`.
- **Certainty Factor**: Akurasi yang didapatkan adalah `5.18%`.

### Perbandingan
- "Naive Bayes Classifier lebih akurat daripada Certainty Factor."

## Google Colab - Link
https://drive.google.com/file/d/1PBjeTFXp0x-U6XfqPeoNBtfONK9Ay4RG/view?usp=sharing
