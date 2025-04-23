# Fine-Tuning BERT for URL Classification

This project focuses on binary classification of URLs using Transformer models. It demonstrates how to:
- Fine-tune a pre-trained BERT model on a URL classification dataset ([Dataset](https://huggingface.co/datasets/shawhin/phishing-site-classification))
- Compress the model using **knowledge distillation** with DistilBERT
- Further reduce the model size using **4-bit quantization** (Post Training Method)

## 🚀 Results

| Model           | Accuracy | Parameters | Size Reduction |
|----------------|----------|------------|----------------|
| BERT (Teacher) | 89.3%    | 110M       | —              |
| DistilBERT (Student, KD) | 91.3%    | 52.8M       | ↓ 52%         |
| Quantized DistilBERT (4-bit) | 90.8% | 52.8M       | —        |

So, final model has better accuracy with fewer parameters and smaller size than the initial model.

## Key Techniques

- **Fine-Tuning**: Used Hugging Face `Trainer` API to fine-tune `bert-base-uncased` on binary URL data.
- **Knowledge Distillation**: Trained a DistilBERT student model using logits from the BERT teacher model for improved performance with fewer parameters.
- **Model Quantization**: Applied 4-bit NF4 quantization using `bitsandbytes` to reduce memory footprint and enable deployment on low-resource devices.
