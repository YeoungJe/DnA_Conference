# 제 1회 D&amp;A Conference - 음악을 쓰다  
국민대 빅데이터 분석 학회 'D&A'에서 진행한 '음악을 쓰다'는 기계학습을 통해 음악을 악보로 변환하는 프로젝트입니다. 

사용 툴 : Python  
사용 프레임 워크 : Keras  
프로젝트 목적 : 머신러닝, 딥러닝을 활용한 음악 to 악보 프로젝트  
프로젝트 기간 : 2018.09~2018.11


## 개요  
프로젝트 간략한 개요는 다음과 같습니다.  
* Python의 librosa library를 활용하여 음을 Spectrogram으로 변환하여 음이 변하는 지점을 추출 및 저장합니다.  
* Spectrogram으로 변환된 데이터는 KNN-PCA-DBSCAN의 과정을 거쳐 cleansing과정을 거칩니다.  
* 정제된 데이터를 바탕으로 CNN을 적용합니다.  
  

## 단계별 적용 과정
* KNN Algorithm : 피아노 음은 무수히 많은 조합의 수가 존재합니다. 따라서 모든 음을 데이터로 사용하는 것은 학습에 장애를 줄 수 있다 판단하였습니다. KNN을 통해 많이 눌리지 않은 특수한 음 조합은 가장 유사하며 대표성을 띄는 음에 할당하여 Label 축소역할을 진행하였습니다.  
* PCA Algorithm : Spectrogram이 음별로 잘 추출되었는지 확인하기 위해 2차원으로 시각화 과정을 거칩니다. 이후 Label마다 Outlier를 제거를 하게됩니다. 이때 모든 경우의 수를 사람이 직접 판단할 수 없어서 다음 과정을 거칩니다.  
* DBSCAN Algorithm : PCA를 통해 2차원으로 시각화 한 후 Outlier를 제거하는 과정을 모든 Label에 자동으로 적용하기 위한 과정입니다. 밀도기반 군집화인 DBSCAN를 이용하여 Main cluster의 core data를 제외한 나머지 data는 Outlier로 판단하여 제거하는 과정입니다.  
* CNN Model : 위의 각 단계를 거친 후 정제된 데이터를 학습시킵니다. Multi-label Classification의 문제였기에 마지막 layer의 활성함수를 softmax 대신 sigmoid로 변경합니다.  

## 이미지  
![음쓰1](https://user-images.githubusercontent.com/48852089/54863255-d15e7e80-4d89-11e9-9f2b-524446c0e034.png)

## 스크립트 소개
* [WM_01] 1.Make training data - MIDI파일에서 CNN 학습을 위한 스펙트로그램을 추출 및 저장  
* [WM_01] 2.Modeling - CNN 모델링  
* [WM_01] 3.Convert mp3 to midi - 학습된 모델을 바탕으로 mp3파일을 midi파일(악보를 만들기 위한 파일)로 변환  
* [WM_01] 4.Meaching Learning part - KNN-PCA-DBSCAN-CNN으로 이어지는 스크립트  

## 프로젝트 팀원
국민대 빅데이터 경영통계학과 14 김동현, 14 임진혁, 14 최영제
