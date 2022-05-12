# Capstone: Detecting Manufacturing Nonconformities through Live Video Deep Learning Classification<br>

Link to PPT Presentation: https://docs.google.com/presentation/d/1ephVxvmPIsCCfeQlDyYWQEQTdZi4_28f/edit?usp=sharing&ouid=108322747122188653599&rtpof=true&sd=true

## Problem Statement

To implement a Live Video Deep Learning Classification Model to effectively detect product defects and procedural non-conformities in the Manufacturing Production Line.

## Executive Summary

As a Manufacturing Quality Data Scientist, I, together with a task force, was tasked to investigate a Customer return merchandise authorization (RMA) event relating to a defect in one of our newly released products. Upon investigation, we found that there was a random periodical procedure non-conformance which was undetected and led to the Customer receiving the poor-quality product.

In the interim while the Manufacturing Process Engineer devise a more permanent solution, I was tasked to produce a Computer Vision Deep Learning solution that is effective in screening out non-conforming products and deviations specific to the investigated root cause to prevent further Quality escapes.

Images of Lego® blocks mimicking Manufacturing Product Assembly was obtained from a webcam installed on a personal computer in order to train and develop the model. A customised Convolutional Neural Network (CNN) that utilised fixed Regions of Interests (ROIs) was developed in order to effectively screen out poor quality products through Live Video Classification.

After an effective model was developed, recommendations on model implementation to Manufacturing Production Line were proposed and elaborated.

Link to Screen Capture of Proposed Implementation to Production Workstation PC (Ongoing Assembly Live Video Classification): https://drive.google.com/file/d/1dDS_45bm24q8aYMPldSqLOKJiNfSgnXb/view?usp=sharing


## System and Software Versions
**Note**
This code was run on a personal computer with the following specifications:

CPU: AMD Ryzen 9 3950X 16-Core Processor 3.49 GHz
RAM: 64 GB Crucial 3200MHz CL16
GPU: NVIDIA RTX3080Ti
Storage: ADATA SX8200 1TB NVME Gen 3

The following was installed to run the code:

cudatoolkit 11.2.2
cudnn 8.1.0.77
keras 2.6.0
keras-applications 1.0.8
keras-preprocessing 1.1.2
matplotlib 3.5.1
numpy 1.19.5
opencv 4.5.5
pillow 9.0.1
python 3.8.12
seaborn 0.11.2
scikit-learn 1.0.2
tensorflow 2.6.3
tensorflow-gpu 2.6.3
tensorflow-hub 0.12.0
tflearn 0.5.0