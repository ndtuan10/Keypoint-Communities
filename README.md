# Keypoint-Communities (Zauss et al., 2021)

# Selected Topics in Computer Vision - CS420.M11.KHCL

 ![uitlogo](https://portal.uit.edu.vn/Styles/profi/images/logo186x150.png)

Contents of final project of Selected Topics in Computer Vision (Các vấn đề chọn lọc trong thị giác máy tính) - CS420

## **Introduction to Keypoint Communities**
- [SOTA for 2D Human Pose Estimation on COCO WholeBody](https://paperswithcode.com/sota/2d-human-pose-estimation-on-coco-wholebody-1?p=keypoint-communities)
- [SOTA for Car Pose Estimation on ApolloCar3D](https://paperswithcode.com/sota/car-pose-estimation-on-apollocar3d?p=keypoint-communities)
- [ICCV 2021 paper](https://openaccess.thecvf.com/content/ICCV2021/papers/Zauss_Keypoint_Communities_ICCV_2021_paper.pdf)
- [Source code](https://github.com/DuncanZauss/Keypoint_Communities)

## **Introduction to data**
### **Data used in paper**
#### **COCO WholeBody (Jin et al., 2020)**
- The first dataset for whole-body evaluation and is an extended version of the 2017 COCO dataset. There are four boundaries available on humans: person box, face box, left-hand box and right-hand box. 
- This dataset includes annotations with 64000 training images and 5000 COCO validation images for face, hands and feet. A full person pose contains 133 keypoints, including 17 for the body, 6 for the legs, 68 for the face and 42 for the arms, along with 152 connections.
- [COCO WholeBody paper](https://arxiv.org/abs/2007.11858)
#### **ApollorCar3D (Song et al., 2018)**
- ApolloCar3D is a dataset that contains 5,277 driving images and over 60K car instances, where each car is fitted with an industry-grade 3D CAD model with absolute model size and semantically labelled keypoints. This dataset is above 20 times larger than PASCAL3D+ and KITTI, the current state-of-the-art.
- [ApolloCar3D paper](https://arxiv.org/abs/1811.12222)
### **Data we use to evaluate Zauss's method**
#### **CrowdPose (Li et al., 2019)**
- Dataset contains 10K training images, 8000 validation images, 2000 test images for a total of 80K human poses and the number of keypoints is labeled as 14.
- [CrowdPose paper](https://arxiv.org/abs/1812.00324)

## **Evaluation**
### **Evaluation on COCO WholeBody**
_ |WB |body |foot |face |hand
--- | --- | --- | --- | --- | ---
AP | 60.4 | 69.6 | 63.4 | 85.0 | 52.9
AP (0.5) | 85.5 | 88.1 | 80.0 | 95.4 | 78.5
AP (0.75) | 66.2 | 76.1 | 68.0 | 89.2 | 57.7
AP (M) | 47.4 | 57.7 | 46.0 | 57.4 | 18.0
AP (L) | 67.8 | 77.5 | 71.4 | 92.4 | 57.0

### **Evaluation on ApollorCar3D**
_ |WB
--- | --- |
AP | 64.2 |
AP (0.5) | 80.1 |
AP (0.75) | 69.7 |
AP (M) | 59.1 |
AP (L) | 82.3 |
Detection rate | 89.6 |

### **Evaluation on CrowdPose**
_ |WB
--- | --- |
AP | 66.2 |
AP (0.5) | 86.6 |
AP (0.75) | 71.0 |
AP (M) | 52.8 |
AP (L) | 70.0 |

## **Testing**
- For human pose estimation
```
python -m openpifpaf.predict /content/IMG_0610.jpg --checkpoint=shufflenetv2k30-wholebody --line-width=2 --show --save-all
```
- For car pose estimation
```
python -m openpifpaf.predict /content/Tuan.jpg --checkpoint=shufflenetv2k30-apollo-66 --image-dpi-factor=0.25 --line-width=2 --caf-th=0.2 --seed-threshold=0.2 --show --save-all
```
- For video demo
```
python -m openpifpaf.video --source=/content/IMG_0607.mp4 --checkpoint=shufflenetv2k16-wholebody --long-edge=321 --horizontal-flip --show --video-output
```

## **Qualitative results**
### **COCO WholeBody**
![Hình_3.jpg](https://github.com/ndtuan10/Keypoint-Communities/blob/main/demo/%E1%BA%A3nh%20demo/COCO%20WholeBody%20%2B%20ApolloCar3D/output/H%C3%ACnh%203%20(human).jpg)

![Hình_7.jpg](https://github.com/ndtuan10/Keypoint-Communities/blob/main/demo/%E1%BA%A3nh%20demo/COCO%20WholeBody%20%2B%20ApolloCar3D/output/H%C3%ACnh%207.jpeg)

![Hình_10.jpg](https://github.com/ndtuan10/Keypoint-Communities/blob/main/demo/%E1%BA%A3nh%20demo/COCO%20WholeBody%20%2B%20ApolloCar3D/output/H%C3%ACnh%2010.jpeg)

### **ApolloCar3D**
![Hình_3_car.jpg](https://github.com/ndtuan10/Keypoint-Communities/blob/main/demo/%E1%BA%A3nh%20demo/COCO%20WholeBody%20%2B%20ApolloCar3D/output/H%C3%ACnh%203%20(car).png)

![Hình_9.jpg](https://github.com/ndtuan10/Keypoint-Communities/blob/main/demo/%E1%BA%A3nh%20demo/COCO%20WholeBody%20%2B%20ApolloCar3D/output/H%C3%ACnh%209%20(car).png)

![Hình_2.jpg](https://github.com/ndtuan10/Keypoint-Communities/blob/main/demo/%E1%BA%A3nh%20demo/COCO%20WholeBody%20%2B%20ApolloCar3D/output/H%C3%ACnh%202%20(car).jpeg)

### **CrowdPose**
![Hình_3_Crowd.jpg](https://github.com/ndtuan10/Keypoint-Communities/blob/main/demo/%E1%BA%A3nh%20demo/CrowdPose/H%C3%ACnh%201.jpeg)

![Hình_2_Crowd.jpg](https://github.com/ndtuan10/Keypoint-Communities/blob/main/demo/%E1%BA%A3nh%20demo/CrowdPose/H%C3%ACnh%202.jpeg)

### **Video demo**
![Video 1](https://github.com/ndtuan10/Keypoint-Communities/blob/main/demo/video%20demo/output/2.gif)
