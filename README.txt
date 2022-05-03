## Introduction :


The task is to assign a single emotion to the video clip from eight universal emotions—Ryerson audio-visual database of emotional speech and song (RAVDESS). 


Discussion about the dataset :


Information regarding the dataset can be read here: https://www.kaggle.com/datasets/uwrfkaggler/ravdess-emotional-speech-audio


Since the dataset contains duplicates. (Video-audio and video only), hence we will only use half of the dataset, i.e. 1440 video clips of 24 different actors. 




Baseline Implementation 


The baseline implementation uses the idea of implementing audio and video emotion recognition separately. We extract the video frame by frame. OpenCV haar cascade function and face detection algorithm was being used to extract faces from the images. Images are resized into 128 * 128 according to what’s given before. LBP algorithm has been used, taking into account 4 * 4 spatial blocks, and we finally generate 32*32 feature vectors for an image which we have then flattened into a 1024 size vector.
According to the paper, I was supposed to use the openEAR toolkit for audio feature extraction, but that was not available. I tried to use the openSMILE backend and extracted the same but could not finalise the audio code. We have hence tried to use Log-Mel spectrograms as the method of feature extraction. PCA had been used for dimension reduction. SVM has been used as written in the baseline technique for the paper.


Limitations :


1. The baseline technique has not tried to use audio and video together for multimodal emotion detection. Hence, they are not utilising the ability to create more accurate choices.
2. We have kind of corrected the usage in audio. The paper uses both SVM for audio and video emotion classification. Better models are available, and they can be tried for it.
3. We have used the sklearns face detection algorithm, which might not be accurate. We could also have used face_utils, a submodule of imutils, to access our helper function.


Improvements :
We would use better models for emotion classification in the dataset. This can be done using a multilayer perceptron for both image and audio. The best way to have high accuracy and precision is to somehow use classifications and feature vectors from both image and audio. We can do this by using the idea of early fusion, wherein we will integrate feature vectors (i.e., audio and video) of separate modalities.








References :


https://www.geeksforgeeks.org/create-local-binary-pattern-of-an-image-using-opencv-python/
https://pyimagesearch.com/2017/04/03/facial-landmarks-dlib-opencv-python/
https://towardsdatascience.com/speech-emotion-recognition-using-ravdess-audio-dataset-ce19d162690#:~:text=It%20is%20a%20system%20through,field%20or%20customer%20call%20centers.
https://www.coursera.org/learn/introduction-computer-vision-watson-opencv/home/welcome
https://github.com/maelfabien/Multimodal-Emotion-Recognition
https://audeering.github.io/opensmile/get-started.html
