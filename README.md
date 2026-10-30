# ASSIGNMENT DAY 10: INITIAL AI FEATURE PIPELINE ANALYSIS

## Proyek Final: PANGANITA — Sahabat Gizi & Panen Ibu Nusantara

**Fitur AI Pertama:** RAG Chatbot "Bu Nita AI" (Konseling Gizi 1.000 HPK & Olahan Pangan)

**Fitur AI Kedua:** Computer Vision (Pindai dan Deteksi Bahan Pangan Menggunakan YOLO26)

---

## Identitas Tim Pengembang

- **Kelompok:** 10 (Malahayati)
- **Penanggung Jawab RAG Chatbot:** Prawita Mepilianti & Deasy Matakupan
- **Computer Vision:** Dita Surya Kartika & Aulya Rakhmawati

**Kolaborasi Anggota:**
- Frontend Chatbot: Prawita Mepilianti.
- Database: Aulya Rakhmawati.
- Computer Vision: Dita Surya Kartika & Aulya Rakhmawati.
- RAG Chatbot: Deasy Matakupan & Prawita Mepilianti.

---

## 1. Problem Statement

PANGANITA dikembangkan untuk membantu perempuan produsen pangan dalam mengelola hasil panen guna mendukung pemenuhan gizi keluarga dan pencegahan stunting pada 1.000 Hari Pertama Kehidupan (HPK).

Dua permasalahan utama yang ingin diselesaikan:

1. **Kesulitan memperoleh konsultasi gizi harian.** Ibu membutuhkan informasi mengenai MPASI, kebutuhan gizi anak, pengolahan pangan lokal, dan pencegahan stunting secara praktis.
2. **Belum optimalnya pemanfaatan hasil panen.** Keluarga sering menghadapi dilema antara menjual hasil panen untuk memperoleh pendapatan dan menyisihkan bahan pangan bergizi untuk kebutuhan keluarga.

### Pengguna Sasaran

- Ibu hamil dan ibu menyusui.
- Orang tua dengan anak usia 6–24 bulan.
- Perempuan produsen pangan dan keluarga petani.
- Kader Posyandu.

## 2. Fitur AI yang Dipilih

### A. RAG Chatbot – Bu Nita AI 

Chatbot berbasis Retrieval-Augmented Generation yang membantu pengguna memperoleh informasi seputar gizi 1.000 HPK, MPASI, pengolahan pangan lokal, dan pemanfaatan hasil panen.

**Teknologi:** FastAPI, ChromaDB, Sentence Transformers, dan Gemini 2.5 Flash.

### B. Computer Vision – Pindai Panen 

Fitur untuk mengenali dan mendeteksi bahan pangan berdasarkan foto yang diunggah pengguna.

**Model:** YOLO26n Detection yang telah melalui proses fine-tuning menggunakan dataset PANGANITA.

Model mengenali 15 kelas bahan pangan, yaitu wortel, udang, singkong, pisang, ubi jalar, jagung, tomat, ikan lele, ikan kembung, ikan tongkol, ikan gurame, bayam, kangkung, buah naga, dan telur ayam ras.

Hasil deteksi dapat menjadi dasar pemilihan bahan pangan dalam simulasi pembagian hasil panen.

## 3. Data atau Input yang Digunakan

**RAG Chatbot:**
- Dokumen PDF sebagai sumber pengetahuan.
- Pertanyaan pengguna sebagai input percakapan.
- Embedding menggunakan Sentence Transformers.

**Computer Vision:**
- Foto bahan pangan lokal.
- Dataset gambar dengan anotasi format YOLO.
- Dataset training, validation, dan testing.

## 4. Alur Pipeline AI

### A. RAG Chatbot

```text
Dokumen PDF
     ↓
Text Extraction
     ↓
Chunking
     ↓
Embedding
     ↓
ChromaDB
     ↓
User Query
     ↓
Retrieval
     ↓
Gemini LLM
     ↓
Jawaban Chatbot
```

### B. Computer Vision

```text
Gambar Bahan Pangan
        ↓
Preprocessing
        ↓
Dataset dan Anotasi YOLO
        ↓
Fine-tuning YOLO26n
        ↓
Pengujian Model
        ↓
Prediksi Gambar
        ↓
Nama Kelas dan Bounding Box
```

## 5. Implementasi Awal

**RAG Chatbot:**
Pengembangan antarmuka Bu Nita AI menggunakan Next.js serta integrasi backend FastAPI, ChromaDB, dan Gemini.

**Computer Vision:**
Eksperimen utama dilakukan melalui notebook `eksperimen_yolo26_detect.ipynb`, mencakup persiapan dataset, training, pengujian, dan prediksi menggunakan model YOLO26n Detection.

## 6. Keterbatasan dan Pengembangan Selanjutnya

- RAG membutuhkan dokumen sumber yang relevan dan tervalidasi agar jawaban dapat dipercaya.
- Computer Vision masih membutuhkan penambahan variasi dataset dan evaluasi performa deteksi.
- Integrasi kedua fitur perlu dikembangkan agar hasil deteksi bahan pangan dapat mendukung informasi gizi dan simulasi pembagian hasil panen.

**Tujuan akhir:** Mengintegrasikan Bu Nita AI dan Pindai Panen sebagai fitur pendukung pengambilan keputusan pangan dan gizi keluarga dalam aplikasi PANGANITA.