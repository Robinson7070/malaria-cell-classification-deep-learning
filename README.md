# Malaria Cell Image Classification — Deep Learning Study

A progressive three-model deep learning pipeline for automated 
malaria parasite detection from microscopy images.

**Best result: 96.52% accuracy | 97.68% recall on 4,134 test images**

---

## Models Implemented

| Model | Accuracy | Precision | Recall | F1-Score | Params |
|-------|----------|-----------|--------|----------|--------|
| Custom CNN (baseline) | 96.52% | 95.46% | 97.68% | 96.56% | 8.4M |
| EfficientNetB3 (transfer learning) | 95.82% | 95.14% | 96.57% | 95.85% | 11.2M |
| Vision Transformer (ViT) | 85.73% | 88.17% | 82.54% | 85.26% | 3.4M |

---

## Why This Problem Matters

Malaria kills over 600,000 people annually, predominantly in 
sub-Saharan Africa. Manual microscopic diagnosis is time-consuming, 
expertise-dependent, and prone to fatigue-related error. This project 
builds automated deep learning systems that could support diagnosis 
in resource-limited settings.

**Clinical framing:** False negatives (missed infections) = untreated 
patients. Recall is therefore the most important metric — the Custom 
CNN's 97.68% recall means only 96 of 4,134 test cases were missed.

---

## Technical Highlights

- **Three architecturally distinct models** compared systematically: 
  baseline CNN, transfer learning, and attention-based transformer
- **Two-phase EfficientNetB3 fine-tuning:** frozen base → selective 
  unfreeze of top 30 layers at reduced learning rate
- **Vision Transformer from scratch:** patch embedding, 6 encoder 
  blocks, 8-head self-attention, CLS token classification
- **Grad-CAM explainability** for CNN and EfficientNetB3 — confirms 
  models focus on the purple-stained parasite region, not artefacts
- **Attention Rollout** for ViT — propagates attention across all 6 
  encoder layers to identify attended patches
- **Clinically valid evaluation:** precision, recall, F1, confusion 
  matrices with false n
