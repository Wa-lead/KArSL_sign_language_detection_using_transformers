
## Project Description
Predicting sign language on the KArSL data using Media Pipe pre-processing and transformers.

## Installation
1. > git clone https://github.com/Wa-lead/KArSL_sign_language_detection_using_transformers.git
2. > pip install -r requirements.txt

## Usage
1. Select a video from the data/... folder
2. Paste it into the inference part in 'src/main.ipynb'

## Overview

### Data Preprocessing

This repository includes the necessary data preprocessing steps to prepare the dataset for model training. The following steps are performed:

1. **Build feature extractor**: The code defines a function to build a feature extractor using the InceptionV3 model. This feature extractor is responsible for extracting important features from the images.

2. **Prepare the data**: The data preprocessing involves extracting hand pose estimations using MediaPipe. The code utilizes the MediaPipe library to detect and extract hand landmarks from the images. The images are then resized to the desired size and normalized. The feature extractor is applied to the preprocessed images to extract the features.
![output](https://github.com/Wa-lead/KArSL_sign_language_detection_using_transformers/assets/81301826/8819866e-a4ac-4c47-9ec7-11378544b258)

3. **Postprocessing**: The postprocessing step includes handling imbalanced labels by padding the data to ensure that each label has the same number of samples. Additionally, some videos may have a different number of frames, so padding is applied to make all videos have the same number of frames.

4. **Create the validation set**: A validation set is created by moving a specified percentage of samples from the training set to the validation set. This helps evaluate the model's performance during training.

Please refer to the respective sections of the code for more details on each preprocessing step.

For the complete code and further model building steps, please refer to the `main.ipynb` notebook in this repository.

### Model Building
There are two tasks that are performed in this project:
1. Testing the model performance on signer-dependent data (i.e. the signer is the same for both training and testing)
2. Testing the model performance on signer-independent data (i.e. the signer is different for training and testing)

#### Results

##### Signer dependent 
| Signer |  Accuracy |
| --- |  --- |
| 01 | 93.2% |
| 02 | 92.9% |
| 03 | 99.0% |

##### Signer independent
| Signer |  Accuracy |
| --- |  --- |
| 01 ( trained on 02, 03) | 63.9% |
| 02 ( trained on 01, 03) | 60.9% |
| 03 ( trained on 01, 02) | 60.4% |

### Inference
* Actual: Respiratory device
* Predicted: {'Respiratory device': 0.98886746, 'laser ray': 0.0033606067, 'surgery': 0.0029914808}
  
![75283300](https://github.com/Wa-lead/KArSL_sign_language_detection_using_transformers/assets/81301826/326588a7-6627-4147-a334-d10e20478e9c)

## Dataset ( link )
[KArSL](https://dl.acm.org/doi/pdf/10.1145/3423420)
