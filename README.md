# Plasmodium Life Stage Detection

Detection and classification of Plasmodium falciparum life stages 
from Giemsa-stained blood smear images using YOLO26m.

Detects three classes Ring, Trophozoite, and Schizont.

---

## Model and Full Documentation

The trained model, evaluation results, training curves, 
and full model card are available on Hugging Face:

[huggingface.co/kenyanmalarai-detect](https://huggingface.co/kenyanmalarai-detect)

---

## Quick Start
```python
from huggingface_hub import hf_hub_download
from ultralytics import YOLO

weights_path = hf_hub_download(
    repo_id  = "kenyanmalarai-detect",
    filename = "weights/best.pt"
)

model   = YOLO(weights_path)
results = model.predict("your_image.jpg", conf=0.15, imgsz=512)
results[0].show()
```


