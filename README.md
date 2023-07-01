# Detection-of-Covid19-Using-Lung-Ultrasound
### Abstract 
X-Ray and CT scans are widely used for identifying COVID-19 but they are neither fast nor cost-effective or widely accessible in contrast, ultrasound has the advantages of quickness and affordability and is widely accessible. In this work, we are processing the videos of the lung ultrasound. An average of 152 frames are extracted from the video data of the lung ultrasound. The extracted frames of the dataset are then taken and fed to CNN/Vision Transformer Models. The vision transformer split the frames into fixed-size patches, each of them is then linearly embedded, position embedding is added and the resulting sequence of vectors is fed to a standard transformer encoder. CNN (Convolutional Neural Network) or ConvNet is a class of Neural networks that specializes in processing data that has a grid-like topology, such as an image. Digital images are the binary representation of visual data. In its pixels are arranged in a grid-like fashion that contains pixel values to denote how bright and what type of colour each pixel should have. The result of both CNN and Vision transformer in a single architecture for increasing efficiency of the model. 
 
### 1. Introduction 
A vital need for quick testing and diagnosis of patients has been overserved during the COVID-19 pandemic. While the X-Ray and CT scans are available for identifying COVID-19 but they are not fast either cost-effective or widely accessible, whereas the ultrasound provides the advantages of quickness, affordability and it is widely accessible to all moreover it can be useful for diagnose acute respiratory distress syndrome in a patient during COVID-19. Even though ultrasound is providing all these advantages the use of ultrasound is less in this field. We are working with videos of lung ultrasound. The video data of lung ultrasound consisted of three different classes (COVID-19, pneumonia, and healthy). Lately, in computer vision research, transformers are showing similar and out-performing traditional CNN Models. In this paper, we are working with a transformer model for COVID-19 Detection using lung ultrasound and report their performance while comparing it with the traditional CNN model.  

### 2. Problem Statement 

●	 Comparing the result of the image transformer model to CNN. 

●	Trying different ensemble schemes for comparing transformer and CNN model. 

### 3. Objectives  

Recent development shows the performance of transformers is like or outperforms CNN-based models in many computer vision tasks so comparing the result of the image transformer model to CNN is important as well as a necessity because it can give insights on developing more efficient models to detect covid from lung ultrasound. 
 
It is well known in the field of machine learning that combining different models usually gives better performance compared to each individual model also known as Ensembling. Ensembling both diversity and similar individual model performance are important. CNN and Transformer-based computer vision models check both the points hence applying CNN + Transformer Model is Important. 

### 4. Methodology  

In the code,using the pocus videos from the GitHub repository  “https://github.com/jannisborn/covid19_ultrasound/tree/master/data”. We have three different labels (covid-19, pneumonia, and healthy). Then we encode the labels (covid-19=2, pneumonia=1, and healthy=0). In the dataset file, the name has been given but its extension has not been given. In video data, there are several different extensions were present. Then we loop through all the possibilities to find the video name if it has existed in the dataset. If the video name exists in the dataset, then we append its path and labels in a data frame. Later, we extracted every frame from each video and save the path in a new data frame with the video format of F “/data/video_{i}_framed, jpg.” We have got about 20,000 frames. Then we stored the video id in a particular frame to which it belongs.  

In some papers,noticed that the researcher has split the data at the frame level, due to which creates a data leak for example frame0 and frame1 of a video are almost identical. But it can get in train and test set, which make the task meaningless. So, we divide the frames at the video level so that all the frames of a particular video will either belong to the train set or test set but will not belong to both sets. In this code, we are using the following augmentation as Resize, Random, Brightness Constrict, CLAHE, Gauss Noise, and Normalize.   

We are currently using vit_ting_pat_ch16_224 modal from Timm. It requires the image size to be 224x224. So, we must resize the images. Then we are loading the pre-trained weights and change the head. The models have three outputs. Then we have PyTorch train and valid loop to train the modal and check the score. While doing the valid loop we calculated the score by averaging the probabilities of all the frames of a single video. Till now we have done this much but, in the future, we will optimize the modal and we will try different assembly methods for both transformer and CNN. 
![image](https://github.com/Piyush23445/Detection-of-Covid19-Using-Lung-Ultrasound/assets/89131804/782c16aa-e6c5-4db3-b094-6c7adbe1d1ea)

### 5.Result

IMAGE CNN ACCURACY : 0.8670772004%

VIDEO CNN ACCURACY : 0.8257575758%

IMAGE TRANSFORMER ACCURACY : 0.8235205767%

VIDEO TRANSFORMER ACCURACY : 0.553030303%

### 6.Conclusion
Assembled two models: the CNN model and the transformer vision model. After performing all the operations, it gives a resulting output, which shows the CNN model performance is better than the transformer vision model performance. In the future, if we do research then the performance of transformer vision can also improve.

#### References  

[1]	Born Jannis, Nina Wiedemann, Manuel Cossio, Charlotte Buhre, Gabriel Brändle, Konstantin Leidermann, Julie Goulet et al. "Accelerating detection of lung pathologies with explainable ultrasound image analysis." Applied Sciences 11, no. 2 (2021): 672.

[2]	David Chen (2021) Analysis of Machine Learning Methods for COVID-19 Detection Using Serum Raman Spectroscopy, Applied Artificial Intelligence, 35:14, 1147-1168 

[3]	Diaz-Escobar, J., Ordóñez-Guillén, N. E., Villarreal-Reyes, S., Galaviz-Mosqueda, A., Kober, V., Rivera-Rodriguez, R., & Rizk, J. E. L. (2021). Deep-learning based detection of COVID-19 using lung ultrasound imagery. Plos one, 16(8), e0255886.

[4]	Ebadi, S. E., Krishnaswamy, D., Bolouri, S. E. S., Zonoobi, D., Greiner, R., Meuser-Herr, N., ... & Punithakumar, K. (2021). Automated detection of pneumonia in lung ultrasound using deep video classification for COVID-19. Informatics in Medicine Unlocked, 25, 100687.

[5]	Barros, B., Lacerda, P., Albuquerque, C., & Conci, A. (2021). Pulmonary COVID-19: Learning spatiotemporal features combining cnn and lstm networks for lung ultrasound video classification. Sensors, 21(16), 5486.

[6]	Camacho, J., Muñoz, M., Genovés, V., Herraiz, J. L., Ortega, I., Belarra, A., ... & Tung-Chen, Y. (2022). Artificial Intelligence and Democratization of the Use of Lung Ultrasound in COVID-19: On the Feasibility of Automatic Calculation of Lung Ultrasound Score. International Journal of Translational Medicine, 2(1), 17-25.

[7]	 Frank, O., Schipper, N., Vaturi, M., Soldati, G., Smargiassi, A., Inchingolo, R., ... & Bagon, S. (2021). Integrating domain knowledge into deep networks for lung ultrasound with applications to COVID-19. IEEE transactions on medical imaging, 41(3), 571-581.

[8]	Perera, S., Adhikari, S., & Yilmaz, A. (2021, September). Pocformer: A lightweight transformer architecture for detection of covid-19 using point of care ultrasound. In 2021 IEEE International Conference on Image Processing (ICIP) (pp. 195-199). IEEE.
