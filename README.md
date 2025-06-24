
---

# Prediksi Keputusan Pengadilan Negeri dan Mahkamah Agung Terkait Kasus Pidana Pemalsuan Uang

Proyek ini mendemonstrasikan proses bertahap untuk menganalisis kasus hukum, yang terbagi menjadi lima tahapan. Berikut adalah gambaran umum dari skrip pada setiap tahapan.

## Daftar Isi

1. [Tahap 1: Konversi PDF ke Teks](#tahap-1-konversi-pdf-ke-teks)
2. [Tahap 2: Representasi Kasus](#tahap-2-representasi-kasus)
3. [Tahap 3: Pencarian Kasus](#tahap-3-pencarian-kasus)
4. [Tahap 4: Penggunaan Kembali Solusi](#tahap-4-penggunaan-kembali-solusi)
5. [Tahap 5: Visualisasi Model](#tahap-5-visualisasi-model)

## Anggota Kelompok

1. **Nilton Is Marcal** - 202210370311181
2. **Ilham Wijaya Kusuma** - 202210370311199

## Tahap 1: Konversi PDF ke Teks

**File**: `tahap_1_(convert_pdf_to_txt).py`

Tahap ini bertujuan untuk mengekstrak dan membersihkan teks dari dokumen PDF hukum. Skrip ini melakukan hal-hal berikut:

* Mengunduh dokumen.
* Mengekstrak teks dari file PDF menggunakan `pdfminer`.
* Membersihkan teks yang diekstrak dengan menghapus elemen yang tidak perlu (header, footer, watermark).
* Memvalidasi kualitas teks yang diekstrak.

Skrip ini mendukung pengolahan dokumen PDF dan HTML, memastikan bahwa hanya teks yang valid dan bersih yang disimpan.

### Persyaratan:

* `pdfminer.six`
* `beautifulsoup4`

---

## Tahap 2: Representasi Kasus

**File**: `tahap_2_case_representation.py`

Tahap ini mengolah teks kasus hukum yang telah dibersihkan menjadi format yang terstruktur untuk analisis lebih lanjut. Skrip ini:

* Mendefinisikan dataclass `LegalCaseStructure` untuk merepresentasikan atribut kasus (misalnya nomor perkara, jenis perkara, pihak yang terlibat, pasal yang relevan).
* Mengekstrak bagian-bagian penting seperti fakta, posita, petitum, dan amar putusan dari teks kasus.
* Menyimpan kasus yang telah terstruktur dalam format CSV dan JSON.

Skrip ini juga menghitung berbagai fitur seperti jumlah kata, jumlah kalimat, dan kata kunci dari teks kasus.

---

## Tahap 3: Pencarian Kasus

**File**: `tahap_3_case_retrieval.py`

Tahap ini mempersiapkan kasus yang telah diproses untuk pencarian berdasarkan kesamaan. Skrip ini:

* Memuat dan memproses data.
* Menggunakan vektorisasi TF-IDF dan embedding BERT untuk mengubah teks menjadi representasi fitur.
* Menerapkan model klasifikasi seperti Logistic Regression, SVM, dan Naive Bayes untuk mengevaluasi kinerja menggunakan cross-validation.
* Mendefinisikan fungsi untuk mengambil kasus serupa berdasarkan query, menggunakan model yang telah dilatih.

Tahap ini sangat penting untuk membangun sistem yang dapat mencari kasus relevan berdasarkan query hukum.

---

## Tahap 4: Penggunaan Kembali Solusi

**File**: `tahap_4_solution_reuse.py`

Tahap ini memuat hasil dari tahap sebelumnya dan memanfaatkannya untuk menggunakan kembali solusi dari kasus-kasus yang telah ditemukan sebelumnya:

* Menampilkan model HTML yang telah dilatih dari tahap sebelumnya (melalui Google Drive).
* Tahap ini berfungsi sebagai titik integrasi untuk menggunakan kembali model atau solusi yang dipelajari dari tahap sebelumnya dan menerapkannya pada kasus hukum yang baru.

---

## Tahap 5: Visualisasi Model

**File**: `tahap_5_model_visualization.py`

Tahap ini memvisualisasikan kinerja model machine learning yang digunakan pada tahap sebelumnya. Skrip ini:

* Memuat dataset yang telah diproses.
* Membuat word cloud untuk menganalisis referensi pasal dalam kasus.
* Menggunakan model yang dilatih dengan TF-IDF dan embedding BERT untuk mengevaluasi hasil kasus.
* Memvisualisasikan metrik kinerja seperti F1-Score, akurasi, presisi, dan recall untuk berbagai model.
* Membuat plot untuk hasil cross-validation dan metrik pengujian akhir.

Skrip ini juga mencakup demonstrasi bagaimana menggunakan model terbaik untuk mengambil kasus serupa berdasarkan query uji.

---

## Cara Menggunakan

1. **Instal dependensi**:
   Pastikan bahwa paket Python berikut telah diinstal:

   * `pandas`
   * `numpy`
   * `matplotlib`
   * `seaborn`
   * `sklearn`
   * `torch`
   * `transformers`
   * `wordcloud`
   * `pdfminer.six`
   * `beautifulsoup4`
   * `requests`
   * `nltk`

2. **Jalankan skrip**:
   Eksekusi skrip satu per satu mulai dari Tahap 1 hingga Tahap 5. Setiap tahap bergantung pada tahap sebelumnya, jadi pastikan untuk menjalankannya secara berurutan.

   Contoh:

   ```bash
   python tahap_1_(convert_pdf_to_txt).py
   python tahap_2_case_representation.py
   python tahap_3_case_retrieval.py
   python tahap_4_solution_reuse.py
   python tahap_5_model_visualization.py
   ```

3. **Evaluasi dan visualisasi**:
   Setelah menjalankan semua tahap, Anda akan memiliki pipeline yang berfungsi penuh untuk mengekstrak, memproses, dan menganalisis kasus hukum dengan berbagai model machine learning. Visualisasi pada Tahap 5 membantu Anda mengevaluasi kinerja model.

---


