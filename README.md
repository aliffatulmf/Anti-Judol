<div align="center">

<img src="assets/anti-judol-cover.png" alt="Anti Judol Cover" width="600px">

**Model Klasifikasi Teks Judi Online dalam Bahasa Indonesia**

[![Open Model](https://huggingface.co/datasets/huggingface/badges/resolve/main/model-on-hf-md.svg)](https://huggingface.co/aliffatulmf/deberta-v3-xsmall-anti-judol)
[![Open in Spaces](https://huggingface.co/datasets/huggingface/badges/resolve/main/open-in-hf-spaces-md.svg)](https://huggingface.co/spaces/aliffatulmf/judol-comment-classification)
[![Hugging Face Profile](https://huggingface.co/datasets/huggingface/badges/resolve/main/follow-me-on-HF-md.svg)](https://huggingface.co/aliffatulmf)

</div>

# Anti-Judol DeBERTa: Model Klasifikasi Teks Judi Online

- ### [28/05/2025] Update terbaru dengan deteksi lebih akurat dan lebih ringan dengan ONNX.
  - Model yang dioptimalkan dengan pemahaman bahasa yang lebih baik.
  - Penambahan model `onnx` dengan kuantisasi int8 dan int4 yang lebih ringan.

- ### [24/05/2025] Rilis awal.
  - Berbasis DeBERTA-3-base

## Deskripsi Model

Model ini adalah versi fine-tuned dari [`microsoft/deberta-v3-xsmall`](https://huggingface.co/microsoft/deberta-v3-xsmall) yang dirancang khusus untuk mendeteksi dan mengklasifikasikan konten terkait judi online dalam teks bahasa Indonesia. Model ini membantu mengidentifikasi konten judi yang berpotensi berbahaya untuk mendukung inisiatif keamanan digital dan upaya moderasi konten. Model dapat membedakan antara teks yang terkait judi dan bukan judi dengan akurasi tinggi, menjadikannya berguna untuk sistem penyaringan konten otomatis.

## Penggunaan

- Moderasi konten untuk platform media sosial
- Deteksi otomatis iklan judi
- Penyaringan konten edukatif
- Aplikasi keamanan digital
- Penelitian deteksi konten berbahaya

## Data Pelatihan

Model dilatih menggunakan dataset yang dikurasi berisi sampel teks bahasa Indonesia yang mencakup konten terkait judi dan bukan judi. Dataset mencakup berbagai jenis konten judi seperti iklan kasino online, promosi taruhan olahraga, skema lotere, dan diskusi terkait judi, yang diseimbangkan dengan konten legitim dari berita, media sosial, dan sumber edukatif.

## Hasil Evaluasi

| Step | Training Loss | Validation Loss | F1       |
| ---- | ------------- | --------------- | -------- |
| 50   | 0.676000      | 0.598374        | 0.806867 |
| 100  | 0.439700      | 0.275495        | 0.911765 |
| 150  | 0.240300      | 0.161314        | 0.950226 |
| 200  | 0.135600      | 0.130217        | 0.966767 |
| 250  | 0.120000      | 0.115214        | 0.971168 |
| 300  | 0.098600      | 0.114574        | 0.975758 |
| 350  | 0.071900      | 0.111686        | 0.978788 |

---

**Disclaimer:** Model ini disediakan untuk tujuan penelitian dan edukasi. Pengguna bertanggung jawab untuk memastikan kepatuhan terhadap hukum dan pedoman etika yang berlaku saat menggunakan model ini di lingkungan produksi.
