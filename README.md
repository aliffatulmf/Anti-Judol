<div align="center">

<img src="assets/anti-judol-cover.png" alt="Anti Judol Cover" width="600px">

**MODEL KLASIFIKASI TEKS JUDI ONLINE DALAM BAHASA INDONESIA**

<table><tr>
<td align="center"><a href="https://huggingface.co/aliffatulmf/deberta-v3-xsmall-anti-judol"><img src="https://huggingface.co/datasets/huggingface/badges/resolve/main/model-on-hf-md.svg" alt="Open Model"></a></td>
<td align="center"><a href="https://huggingface.co/spaces/aliffatulmf/judol-comment-classification"><img src="https://huggingface.co/datasets/huggingface/badges/resolve/main/open-in-hf-spaces-md.svg" alt="Open in Spaces"></a></td>
<td align="center"><a href="https://huggingface.co/aliffatulmf"><img src="https://huggingface.co/datasets/huggingface/badges/resolve/main/follow-me-on-HF-md.svg" alt="Hugging Face Profile"></a></td>
</tr></table>

</div>

## Table of Contents

- [Deskripsi](#deskripsi-model)
- [Penggunaan](#penggunaan)
- [Cara Pakai](#cara-pakai)
- [Training Dataset](#training-dataset)
- [Hasil Evaluasi](#hasil-evaluasi)
- [Limitations](#limitations)
- [Changelog](#changelog)
- [License](#license)
- [Citation](#citation)

## Deskripsi

Model ini adalah versi fine-tuned dari [`microsoft/deberta-v3-xsmall`](https://huggingface.co/microsoft/deberta-v3-xsmall) yang dirancang khusus untuk mendeteksi dan mengklasifikasikan komentar judi online dalam bahasa Indonesia, terutama dari platform streaming seperti YouTube. Model ini membantu mengidentifikasi spam judi yang berpotensi berbahaya untuk mendukung inisiatif keamanan digital dan upaya moderasi konten live streaming.

## Penggunaan

- Moderasi komentar live streaming (YouTube, dll)
- Deteksi otomatis spam judi di kolom komentar
- Penyaringan konten judi pada platform video
- Aplikasi keamanan digital untuk streaming platform
- Penelitian deteksi konten berbahaya di media sosial

## Cara Pakai

**Via HuggingFace Transformers:**

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
import torch

tokenizer = AutoTokenizer.from_pretrained("aliffatulmf/deberta-v3-xsmall-anti-judol")
model = AutoModelForSequenceClassification.from_pretrained("aliffatulmf/deberta-v3-xsmall-anti-judol")

text = "🤪𝑫𝑶,𝑹,𝑨,7,7🤪menawarkan cara mudah untuk terhubung dengan orang lain. 🍠"
inputs = tokenizer(text, return_tensors="pt", truncation=True, max_length=128)

with torch.no_grad():
    outputs = model(**inputs)
    prediction = torch.argmax(outputs.logits, dim=1).item()

label = "Judi" if prediction == 1 else "Bukan Judi"
print(f"Hasil: {label}")
```

**Via ONNX (lebih ringan):**

```python
from optimum.onnxruntime import ORTModelForSequenceClassification
from transformers import AutoTokenizer

model = ORTModelForSequenceClassification.from_pretrained("aliffatulmf/deberta-v3-xsmall-anti-judol", file_name="model.onnx")
tokenizer = AutoTokenizer.from_pretrained("aliffatulmf/deberta-v3-xsmall-anti-judol")

inputs = tokenizer("Bandar judi terpercaya, link daftar ada di bio saya", return_tensors="pt", truncation=True, max_length=128)
outputs = model(**inputs)
prediction = outputs.logits.argmax(dim=1).item()
print("Judi" if prediction == 1 else "Bukan Judi")
```

**Demo Interaktif:**

Coba langsung tanpa kode melalui [HuggingFace Spaces](https://huggingface.co/spaces/aliffatulmf/judol-comment-classification).

## Training Dataset

Model dilatih menggunakan **48.000 baris** data yang telah dikurasi dan diolah dari ratusan baris data mentah sebelumnya. Sumber data utama berasal dari komentar dan live streaming platform online, terutama YouTube. Dataset mencakup komentar berbahasa Indonesia yang mengandung konten terkait judi online seperti promosi bandar, link situs judi, dan spam judi, yang diseimbangkan dengan komentar non-judi dari aktivitas normal pengguna.

## Hasil Evaluasi

**Final F1-Score: 0.9788** (step 350)

| Step | Training Loss | Validation Loss | F1       |
| ---- | ------------- | --------------- | -------- |
| 50   | 0.676000      | 0.598374        | 0.806867 |
| 100  | 0.439700      | 0.275495        | 0.911765 |
| 150  | 0.240300      | 0.161314        | 0.950226 |
| 200  | 0.135600      | 0.130217        | 0.966767 |
| 250  | 0.120000      | 0.115214        | 0.971168 |
| 300  | 0.098600      | 0.114574        | 0.975758 |
| 350  | 0.071900      | 0.111686        | 0.978788 |

## Limitations

- Model ini dilatih pada data komentar YouTube dan mungkin tidak optimal untuk platform dengan gaya bahasa yang berbeda.
- Akurasi dapat menurun pada komentar yang sangat pendek atau menggunakan bahasa gaul ekstrem.
- Model hanya memproses teks komentar, tidak memahami konteks visual atau metadata.
- Konten judi yang menggunakan bahasa sandbox, kode, atau sandi mungkin terlewat.

## Changelog

### [28/05/2025] v2.0 - Update ONNX

- Model yang dioptimalkan dengan pemahaman bahasa yang lebih baik.
- Penambahan model `onnx` dengan kuantisasi INT8 dan INT4 yang lebih ringan.

### [24/05/2025] v1.0 - Rilis Awal

- Berbasis DeBERTa-v3-base.

---

**Disclaimer:** Model ini disediakan untuk tujuan penelitian dan edukasi. Pengguna bertanggung jawab untuk memastikan kepatuhan terhadap hukum dan pedoman etika yang berlaku saat menggunakan model ini di lingkungan produksi.

## License

[MIT License](LICENSE)

## Citation

```bibtex
@misc{anti-judol-2025,
  title={Anti-Judol DeBERTa: Model Klasifikasi Teks Judi Online dalam Bahasa Indonesia},
  author={Aliffatul M.F.},
  year={2025},
  publisher={Hugging Face},
  url={https://huggingface.co/aliffatulmf/deberta-v3-xsmall-anti-judol}
}
```
