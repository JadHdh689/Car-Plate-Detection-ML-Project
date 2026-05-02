#  License Plate Detection: A Comparative Study of Object Detection Architectures

> Comparing **YOLOv8n**, **Faster R-CNN**, and **RetinaNet** on 433 car images to find the best license plate detector.

## About

This project tackles license plate detection using three object detection architectures, each representing a different design philosophy:

| Model | Type | Params |
|---|---|---|
| **YOLOv8n** | Lightweight one-stage | ~3M |
| **Faster R-CNN** (ResNet-50 FPN v2) | Two-stage region-based | ~43.7M |
| **RetinaNet** (ResNet-50 FPN v2) | One-stage with focal loss | ~38.2M |

All models were fine-tuned from pretrained weights on the same 303/65/65 train/val/test split using Google Colab's T4 GPU.

## Dataset

[Car Plate Detection](https://www.kaggle.com/datasets/andrewmvd/car-plate-detection) from Kaggle - 433 images with Pascal VOC XML annotations (471 total annotated plates). Labels were converted to YOLO format for training.

## Results

| Model | Precision | Recall | F1 | mAP50 | mAP50-95 |
|---|---|---|---|---|---|
| **YOLOv8n** | **0.9446** | 0.8857 | **0.9142** | 0.9505 | **0.5605** |
| Faster R-CNN | 0.8684 | **0.9429** | 0.9041 | **0.9611** | 0.5452 |
| RetinaNet | 0.8429 | 0.8429 | 0.8429 | 0.8589 | 0.4878 |

*Test set results. Bold = best per metric.*

**Bootstrap analysis** (500 resamples) confirmed that YOLOv8n and Faster R-CNN are statistically tied on mAP50-95 (p = 0.74). YOLOv8n is recommended for its stability, efficiency, and confident predictions.

## Key Takeaways

🏆 **YOLOv8n** - Best precision, F1, mAP50-95. Healthiest training curve. Fewest, most confident detections.

📉 **Faster R-CNN** - Highest recall and mAP50, but overfit by epoch 2.

⚠️ **RetinaNet** - Weakest overall. Plateaued early, collapsed at end of training.

## Tech Stack

`Python` · `PyTorch` · `Ultralytics` · `TorchVision` · `Google Colab`

## Authors

**Jad Hdeife** · **Ahmad El Hariri**


