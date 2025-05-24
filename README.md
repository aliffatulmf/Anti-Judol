<div align="center">

<img src="imgs/anti_judol.png" alt="Anti Judol Cover" width="600px">

**Model Klasifikasi Teks Judi Online dalam Bahasa Indonesia**

[![Open Model](https://huggingface.co/datasets/huggingface/badges/resolve/main/model-on-hf-md.svg)](https://huggingface.co/aliffatulmf/mdeberta-v3-base-anti-judol)
[![Open in Spaces](https://huggingface.co/datasets/huggingface/badges/resolve/main/open-in-hf-spaces-md.svg)](https://huggingface.co/spaces/aliffatulmf/judol-comment-classification)
[![Hugging Face Profile](https://huggingface.co/datasets/huggingface/badges/resolve/main/follow-me-on-HF-md.svg)](https://huggingface.co/aliffatulmf)

</div>

# Anti-Judol DeBERTa-v3-Base: Online Gambling Text Classification Model

## Model Description / Deskripsi Model

**English:**
This model is a fine-tuned version of `microsoft/mdeberta-v3-base` specifically designed for detecting and classifying online gambling-related content in Indonesian text. The model helps identify potentially harmful gambling content to support digital safety initiatives and content moderation efforts. It can distinguish between gambling-related and non-gambling text with high accuracy, making it valuable for automated content filtering systems.

**Bahasa Indonesia:**
Model ini adalah versi fine-tuned dari `microsoft/mdeberta-v3-base` yang dirancang khusus untuk mendeteksi dan mengklasifikasikan konten terkait judi online dalam teks bahasa Indonesia. Model ini membantu mengidentifikasi konten judi yang berpotensi berbahaya untuk mendukung inisiatif keamanan digital dan upaya moderasi konten. Model dapat membedakan antara teks yang terkait judi dan bukan judi dengan akurasi tinggi, menjadikannya berguna untuk sistem penyaringan konten otomatis.

## Intended Uses / Penggunaan yang Dimaksudkan

**English:**
- Content moderation for social media platforms
- Automated detection of gambling advertisements
- Educational content filtering
- Digital safety applications
- Research on harmful content detection

**Bahasa Indonesia:**
- Moderasi konten untuk platform media sosial
- Deteksi otomatis iklan judi
- Penyaringan konten edukatif
- Aplikasi keamanan digital
- Penelitian deteksi konten berbahaya

## How to Use / Cara Penggunaan

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
import torch

# Load model and tokenizer
tokenizer = AutoTokenizer.from_pretrained("aliffatulmf/mdeberta-v3-base-anti-judol")
model = AutoModelForSequenceClassification.from_pretrained("aliffatulmf/mdeberta-v3-base-anti-judol")

# Example text classification
text = "Cuan di ALEXIS17 dijamin gacor."
inputs = tokenizer(text, return_tensors="pt", truncation=True, padding=True, max_length=256)

with torch.no_grad():
    outputs = model(**inputs)
    predictions = torch.nn.functional.softmax(outputs.logits, dim=-1)
    predicted_class = torch.argmax(predictions, dim=-1)

# 0: Non-gambling, 1: Gambling-related
labels = ["Non-Judi", "Judi"]
result = labels[predicted_class.item()]
confidence = torch.max(predictions).item()

print(f"Prediksi: {result} (Confidence: {confidence:.4f})")
```

## Training Data / Data Pelatihan

**English:**
The model was trained on a curated dataset of Indonesian text samples containing both gambling-related and non-gambling content. The dataset includes various types of gambling content such as online casino advertisements, sports betting promotions, lottery schemes, and gambling-related discussions, balanced with legitimate content from news, social media, and educational sources.

**Bahasa Indonesia:**
Model dilatih menggunakan dataset yang dikurasi berisi sampel teks bahasa Indonesia yang mencakup konten terkait judi dan bukan judi. Dataset mencakup berbagai jenis konten judi seperti iklan kasino online, promosi taruhan olahraga, skema lotere, dan diskusi terkait judi, yang diseimbangkan dengan konten legitim dari berita, media sosial, dan sumber edukatif.

## Training Procedure / Prosedur Pelatihan

**Training Hyperparameters:**
- Learning rate: 2e-4
- Batch size: 16
- Number of epochs: 3
- Max sequence length: 256
- LR Scheduler type: cosine
- Weight decay: 0.01

## Evaluation Results / Hasil Evaluasi

| Metric    | Score |
| --------- | ----- |
| Accuracy  | 0.970 |
| Precision | 0.944 |
| Recall    | 0.963 |
| F1-Score  | 0.953 |

## Limitations / Keterbatasan

**English:**
- Primarily designed for Indonesian language text
- May have reduced performance on code-switching or mixed-language content
- Performance may vary with emerging gambling terminology or slang
- Not suitable for detecting sophisticated evasion techniques

**Bahasa Indonesia:**
- Dirancang utamanya untuk teks bahasa Indonesia
- Mungkin memiliki performa yang berkurang pada konten code-switching atau bahasa campuran
- Performa dapat bervariasi dengan terminologi atau slang judi yang baru muncul
- Tidak cocok untuk mendeteksi teknik evasion yang canggih

## Ethical Considerations / Pertimbangan Etis

**English:**
This model is developed to support digital safety and harm reduction efforts. It should be used responsibly and in compliance with local laws and regulations. The model's predictions should be reviewed by human moderators for critical decisions.

**Bahasa Indonesia:**
Model ini dikembangkan untuk mendukung upaya keamanan digital dan pengurangan bahaya. Model harus digunakan secara bertanggung jawab dan sesuai dengan hukum dan regulasi setempat. Prediksi model harus ditinjau oleh moderator manusia untuk keputusan kritis.

## Citation / Sitasi

```bibtex
@misc{anti-judol-deberta-v3-base,
  title={Anti-Judol DeBERTa-v3-Base: Online Gambling Text Classification for Indonesian},
  author={Alif Fatul},
  year={2025},
  publisher={Hugging Face},
  url={https://huggingface.co/aliffatulmf/mdeberta-v3-base-anti-judol}
}
```

---

**Disclaimer:** This model is provided for research and educational purposes. Users are responsible for ensuring compliance with applicable laws and ethical guidelines when deploying this model in production environments.
