﻿
# 04 - Face Recognition - II

## Assignment

1.  Refer to this beautiful  [blog (Links to an external site.)](https://towardsdatascience.com/finetune-a-facial-recognition-classifier-to-recognize-your-face-using-pytorch-d00a639d9a79).
2.  Collect 10 facial images of 10 people you know (stars, politicians, etc). The more the images you collect, the better your experience would be. Add it to this  [LFW (Links to an external site.)](http://vis-www.cs.umass.edu/lfw/lfw-funneled.tgz)  dataset.
3.  Train as in the blog and upload the FR model to Lambda
4.  Share the link to "that" single page.
5.  Share the link to GitHub repo.

## Solution

`160x160` Face Aligned dataset:
[https://github.com/satyajitghana/TSAI-DeepVision-EVA4.0-Phase-2/tree/master/04-FaceRecognition-II/indian_face_dataset_160](https://github.com/satyajitghana/TSAI-DeepVision-EVA4.0-Phase-2/tree/master/04-FaceRecognition-II/indian_face_dataset_160)

**Dataset Creation**: [https://github.com/satyajitghana/TSAI-DeepVision-EVA4.0-Phase-2/blob/master/04-FaceRecognition-II/CustomLFW%26Indian_Face_Dataset.ipynb](https://github.com/satyajitghana/TSAI-DeepVision-EVA4.0-Phase-2/blob/master/04-FaceRecognition-II/CustomLFW%26Indian_Face_Dataset.ipynb)

[The above dataset was then added to LFW Dataset]

LFW-Plus-Dataset (LFW + 10 Indian People): https://drive.google.com/file/d/17k_3guDwSKclVjpyxEmgSmRvB0Z64LCq/view?usp=sharing

Training: 
(Training on LFW + 10 Indian People)
[https://github.com/satyajitghana/TSAI-DeepVision-EVA4.0-Phase-2/blob/master/04-FaceRecognition-II/Train_MTCNN_LFW_Plus.ipynb](https://github.com/satyajitghana/TSAI-DeepVision-EVA4.0-Phase-2/blob/master/04-FaceRecognition-II/Train_MTCNN_LFW_Plus.ipynb)

(Training on 10 faces only)
[https://github.com/satyajitghana/TSAI-DeepVision-EVA4.0-Phase-2/blob/master/04-FaceRecognition-II/Train_MTCNN_Indian_Face.ipynb](https://github.com/satyajitghana/TSAI-DeepVision-EVA4.0-Phase-2/blob/master/04-FaceRecognition-II/Train_MTCNN_Indian_Face.ipynb)

All of the TensorClan Models can be found at https://drive.google.com/drive/folders/15y4WyvaJI9AsfioKUNX1inJtrDqn2UvV?usp=sharing

## Dataset

Indian Faces Dataset
![enter image description here](https://github.com/satyajitghana/TSAI-DeepVision-EVA4.0-Phase-2/blob/master/04-FaceRecognition-II/faces.png?raw=true)

LFW Dataset
![enter image description here](https://github.com/satyajitghana/TSAI-DeepVision-EVA4.0-Phase-2/blob/master/04-FaceRecognition-II/lfw_dataset.png?raw=true)


##  Link [https://thetensorclan-web.herokuapp.com/](https://thetensorclan-web.herokuapp.com/)

**Backend:** [https://thetensorclan-backend.herokuapp.com/](https://thetensorclan-backend.herokuapp.com/)

Code for FrontEnd: [https://github.com/extensive-vision-ai/thetensorclan-web](https://github.com/extensive-vision-ai/thetensorclan-web)
Code for BackEnd: [https://github.com/extensive-vision-ai/thetensorclan-backend-heroku](https://github.com/extensive-vision-ai/thetensorclan-backend-heroku)

## Demo

### LFW - Plus Recognizer (contains 10 additional people)

![enter image description here](https://github.com/satyajitghana/TSAI-DeepVision-EVA4.0-Phase-2/blob/master/04-FaceRecognition-II/demo3.gif?raw=true)

### Indian Faces Recognizer

![enter image description here](https://github.com/satyajitghana/TSAI-DeepVision-EVA4.0-Phase-2/blob/master/04-FaceRecognition-II/demo2.gif?raw=true)

`[right click -> open image in a new tab]` for better experience

## Train Metrics

![enter image description here](https://github.com/satyajitghana/TSAI-DeepVision-EVA4.0-Phase-2/blob/master/04-FaceRecognition-II/train_loss.png?raw=true)

## Explanation

Remember that we had created FaceAlign previously in Face-Recognition-I ? we simply supply our face image to that AWS Lambda API and get the aligned face, now we have added the face recognition model to heroku(why ? see notes), and now its simply matter of sending the aligned face to the model backend and fetching the results ! that's it !

## Notes

- I moved the backend (Flask) to heroku, why ? because AWS has uncompressed requirement to 500MB, and i cannot use PyTorch 1.6.0 with it, something i discussed earlier in previous assignment as well
- Heroku provides a slug size (compressed) python app to 500MB, but even after adding all dependencies my slug size of below 250MB, quite good ain't it ! 

## Personal Notes

- I don't know but, for being a student developer i really like Heroku !, it gives a lot of free things without charging anything ! i can even transfer apps between accounts since every account has 5 apps limit. but a lot of flexibility ! love Heroku !
- AWS is good, don't get me wrong, but too much work, also docker is necessary for lambda, else you WILL face issues, its not the case in Heroku, you simply commit and push to heroku, and rest it will take care ! simply use a build pack of whatever you like.
