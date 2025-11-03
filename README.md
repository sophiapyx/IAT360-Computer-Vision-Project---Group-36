# Feline Pain Detection using YOLOv8
## 1. Project Overview
This computer vision project aims to detect signs of pain in cats using facial expression analysis based on the Feline Grimace Scale (FGS). We utilized YOLOv8n, a supervised object detection model, to classify cat faces into "pain" or "no pain" categories. Our final model (Round 2) focused on improving Recall for the "pain" class through data augmentation and hyperparameter tuning.
## 2. Dataset and Resources
### 2.1. Final Dataset Access (YOLO Format)
Due to file size and the nature of our modified, custom-annotated dataset, the final YOLO-formatted data is provided as a ZIP file. This dataset includes all original data, our newly collected/labeled 60 images, and the augmented data.
Download Link (ZIP File): https://drive.google.com/file/d/1Q4YRALYJRPGGyxsZd7JjKyQgqxhqL0eu/view?usp=sharing
### 2.2. Data Sources and Citations (Required by CC BY-NC 4.0 License)
We acknowledge and cite the original resources used to create our final, derived dataset:
Original Dataset Source：CatFLW dataset (2079 base images) https://www.kaggle.com/datasets/georgemartvel/catflw
Labeling Standard：Feline Grimace Scale (FGS) for annotation guidelines https://www.felinegrimacescale.com
## 3. Setup Guide: Running the Model
Follow these steps to set up the project and reproduce the training/evaluation results:
### 3.1. Clone Repository and Verify Structure
Clone this repository to your local machine.
Verify the required YOLO folder structure (placeholder folders are present):
### 3.2. Dataset Download and Extraction (Crucial Step)
Download: Download the ZIP file from the link provided in Section 2A.
Extract: Extract the ZIP file's contents. The contents will include the images, labels, and pain_augmentation folders.
Placement: Place the extracted folders directly inside the empty /datasets folder of the cloned repository.
### 3.3. Training/Evaluation Configuration
The data.yaml file in the root directory contains the correct paths and class names.
To evaluate the final Round 2 model, use the provided best.pt weights and run the model on your test set
## 4. Key Data Enhancement Note: Duplication Management
During the training for Round 2, we utilized 789 images for pain augmentation. We discovered that this batch accidentally contained images already present in our validation and test sets, which would cause data leakage.
To maintain data integrity, we implemented a near-duplicate detection method (using pHash) to identify and remove images that were too similar to those in the validation/test sets. This process removed 271 images, leaving 518 clean augmented images, which were then exclusively added to the training set for Round 2.