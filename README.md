# Covid Object Detection on X-Ray Images using YOLOv4 and YOLOv5

Object detection is a part of Computer Vision used to locate and classify specific objects within an image. In the medical field, object detection can be applied to chest X-ray images to aid in the detection and localization of respiratory diseases, including COVID-19.

In this project, YOLOv4 and YOLOv5 models were employed for object detection on COVID-19-related chest X-ray images. Based on testing, the size of the images and the model had minimal impact, so smaller sizes were chosen for lighter processing.

Overall results were suboptimal with an mAP of approximately 0.2. Nevertheless, the project provided valuable insights into using YOLOv4 and YOLOv5 with chest X-ray images. It was found that utilizing pre-trained weights accelerates learning but increases the risk of overfitting. Additionally, YOLOv4 demonstrated comparable performance to YOLOv5 despite the latter's faster learning and lighter architecture.

---

### Dataset
The data used originated from Kaggle: [SIIM-FISABIO-RSNA COVID-19 Detection](https://www.kaggle.com/c/siim-covid19-detection/overview). However, the data was in DICOM format, large in size, and not easily accessible. Fortunately, efforts were made to simplify data access. Eventually, [SIIM COVID-19: Resized to 256px JPG](https://www.kaggle.com/xhlulu/siim-covid19-resized-to-256px-jpg) data was used for images and [SIIM-COVID-19 Detection Training Labels](https://www.kaggle.com/ammarnassanalhajali/siimcovid19-detection-training-label) for annotations.

### Code
On Kaggle, numerous codes were available using the SIIM-FISABIO-RSNA COVID-19 dataset, a major prize competition. The primary reference code was [COVID-19 Detection YOLOv5 3Classes](https://https://www.kaggle.com/ammarnassanalhajali/covid-19-detection-yolov5-3classes-training/notebook). From this code, irrelevant components were removed, and new elements were added, such as the inclusion of test data. There was even a critical error in the original code related to label conversion.

### Models
Two models were utilized: YOLOv4 and YOLOv5. For YOLOv5, the original repository from GitHub was used: https://github.com/ultralytics/yolov5. The original YOLOv4 repository was relatively basic, lacking extensive features. Therefore, a modified repository similar to YOLOv5 was employed, compatible with PyTorch: https://github.com/WongKinYiu/PyTorch_YOLOv4/tree/u5. Both models were quite similar, using the same labeling format, facilitating a more accurate comparison. However, it's undeniable that the original YOLOv5 repository is far more advanced than the modified YOLOv4 repository.

### Training and Evaluation
It began with data preprocessing for image and label alignment with the YOLO format. Subsequently, model training commenced, automatically recording various statistics. Evaluation followed to assess training performance and test the model using test data. Finally, comparisons were made based on several metrics from multiple tests.

### WandB
To see some of the results, check this WandB project: https://wandb.ai/pandegaaz/siim-covid19-detect
