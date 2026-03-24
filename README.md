# Plasmodium Life Stage Detection

Detection and classification of *Plasmodium falciparum* life stages 
from Giemsa-stained blood smear images using YOLO26m.

Detects three classes: Ring, Trophozoite, and Schizont.

---

## Progress

| Version | mAP@0.5 | mAP@0.5:0.95 | Accuracy | Notes |
|---------|---------|--------------|----------|-------|
| V1 | 0.735 | 0.513 | 0.63 | Single dataset, 436 test instances |
| V2 | 0.830 | 0.638 | 0.73 | Merged dataset, 759 test instances |

---

## Model and Full Documentation

The trained model, evaluation results, training curves, and full 
development story from V1 to V2 are available on Hugging Face:

[huggingface.co/codeshujaaa/kenyanmalarai-detect](https://huggingface.co/codeshujaaa/kenyanmalarai-detect)

---

## Quick Start
```python
from huggingface_hub import hf_hub_download
from ultralytics import YOLO

# Load V2 model
weights_path = hf_hub_download(
    repo_id  = "codeshujaaa/kenyanmalarai-detect",
    filename = "weights/best_v2.pt"
)

model   = YOLO(weights_path)
results = model.predict("your_image.jpg", conf=0.15, imgsz=640)
results[0].show()
```

---

## Acknowledgements

Dataset by  Roboflow community contributors.  
Training on Kaggle Tesla P100 for V1, Tesla T4 x2 for V2.
