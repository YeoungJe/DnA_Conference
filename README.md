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
  
![음쓰1](https://user-images.githubusercontent.com/48852089/54863255-d15e7e80-4d89-11e9-9f2b-524446c0e034.png)

## 
KNN 알고리즘을 이용하여 가장 비슷한 음으로 할당하여 Label을 축소역할을, PCA를 통해 변환된 Spectrogram을 2차원으로 시각화 후 DBSCAN를 이용하여 Main cluster의 core data를 남기고 나머지 값은 Outlier로 판단하여 제거의 과정을 거칩니다.  
Multi-label Classification의 문제였기에 마지막 layer의 활성함수를 softmax 대신 sigmoid로 변경합니다.

이 프로젝트를 통해 강조하고싶은 점은 알고리즘(KNN, PCA, DBSCAN)들의 상황에 맞는 적용과정입니다. 피아노 음은 무수히 많은 조합의 수가 존재하기 때문에 학습에 장애를 줄 수 있다 판단하여 KNN을 적용하였습니다. KNN을 통해 많이 눌리지 않은 특수한 음 조합은 가장 유사하며 대표성을 띄는 음에 할당하였습니다. 이상치 탐지하기 위해 사람이 하는 과정(눈으로 확인 후 이상치 제거)을 PCA를 이용하여 2차원 축소 후 DBSCAN을 적용하여 최대 군집만을 남겨 자동으로 제거하는 프로세스를 구축하였습니다. 이는 각 알고리즘에 대한 깊이 있는 이해가 있었기에 가능한 작업이라고 생각합니다.
음악을 쓰다 프로젝트를 통해 비정형 데이터 중 음성 데이터를 처리하는 방법을 터득했고 이상치를 제거하는 방법론에 대해 심도있는 고민을 진행하였습니다. 코드와 간략한 진행 과정은 아래 Github 링크를 첨부하였습니다!
 


1. MIDI파일에서 CNN 학습을 위한 스펙트로그램을 추출 및 저장

2. Modeling

3. MIDI파일 생성

국민대 빅데이터 경영통계학과 14 김동현, 임진혁, 최영제
실험
