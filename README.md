# Kaggle-Battle-ground
 캐글 - PUBG Finish Placement Prediction 순위 예측 모델 개발 프로젝트

# 1. 프로젝트 개요

## 1.1 Members 

<div align=center>

|[<img src="https://user-images.githubusercontent.com/73567364/228241695-6c57056c-3a78-46c6-bf22-527a91bc74f5.png" width = "250"/></a>](https://github.com/mg4432)|[<img src="https://avatars.githubusercontent.com/u/73216281?v=4" width = "250"/></a>](https://github.com/kangjun205)|
|:--:|:--:|
|[Mingyu Park](https://github.com/mg4432/)|[Kyungjun Kang](https://github.com/kangjun205)|

</div>

## 1.2 프로젝트 목적
- 기계학습을 통한 **매치 순위에 영향을 미치는 요인 파악**
- 대회 당시(2018)년 리더보드 기준 상위 5% (76/1528) 이상의 성능을 가진 모델 개발 

## 1.3 진행 기간 
- 02/27 ~  3/25
### 주차별 계획
- 1주차(2/27~3/5) : 데이터 내 cheating 유저 파악 & EDA
- 2주차(3/6~3/12) : EDA 기반 Feature Engineering & Baseline 모델 생성, 세부적 분석 방법 조정
- 3주차(3/13~3/18) : 분석 계획에 따른 분석 모델 선정, 생성, 학습 및 고도화
- 4주차(3/19~3/25) : 분석 결과, 분석 방법, 분석 상의 한계점 및 개선사항 정리 후 보고서 작성 
 
![image](https://user-images.githubusercontent.com/73567364/228247433-fb80f097-f4ca-4dce-8a26-8ee172b6e918.png)


## 1.4 Contests
1. Project description
> Project outline, purpose, weekly plan, etc.
2. Project process
> Hypotheses, EDA, feature engineering, model selection, etc.
3. Our strategy
> Stretegies used to develop performance and save time & memory, etc.
4. Result & Conclustion
> Our rank in LB, MAE
> Most effective factors in predicting finish placement.

# 2. Process
## 2.1 Overall process

> Baseline → Pre-processing(& Feature engineering) → Group place → Post-processing

![image](https://user-images.githubusercontent.com/73567364/228247822-7830d064-8b5d-4d6d-9a30-98690f0a23da.png)

## 2.2 Hypotheses 

### 2.2.1 Hypotheses

![image](https://user-images.githubusercontent.com/73567364/228257858-7eaec8a1-d18b-421f-ab0c-d5f848082324.png)

### 2.2.2 Results 

![image](https://user-images.githubusercontent.com/73567364/228258283-8eeca85b-eff8-4257-8691-fb659e6c68e9.png)

![image](https://user-images.githubusercontent.com/73567364/228258358-0e954b55-5ad3-4d7b-a8a8-f5e4035391a9.png)

![image](https://user-images.githubusercontent.com/73567364/228258392-dafed0b9-3e56-4789-b8bf-d860eed61c12.png)

## 2.3 Model selection 

![image](https://user-images.githubusercontent.com/73567364/228258594-bed1762d-d0c2-475e-9c78-d6f6d15581c6.png)

# 3. Our strategy

## 3.1 Reduce memory

- 메모리, 시간을 절약하기 위해 데이터 타입 변경

![image](https://user-images.githubusercontent.com/73567364/228252684-dfcbf94a-eca0-4320-b6b9-9b5149c9707d.png)

## 3.2 Get_group_place :
- killPlace 변수를 통해서 그룹 간의 순위 관계를 추론함.

![image](https://user-images.githubusercontent.com/73567364/228252065-b4cf4ce4-d985-4fec-8b1f-5509c2243095.png)

### 3.2.1 Case 1 : Orders can be inferred exactly

![image](https://user-images.githubusercontent.com/73567364/228252533-d9c9b970-efb4-4c4e-a6d4-799a20143512.png)

### 3.2.2 Case 2 : Orders cannot be inferred exactly

![image](https://user-images.githubusercontent.com/73567364/228252776-7e7d9cbe-7ed7-42a2-bcad-ce582ac3ea29.png)

![image](https://user-images.githubusercontent.com/73567364/228252878-3ccb6525-92b9-4280-85d4-a8dd093c4029.png)  

- **Post-processing** :
![image](https://user-images.githubusercontent.com/73567364/228253557-cd1e88d0-a508-4f0e-a9aa-453d41f4a0c5.png)


# 4. 프로젝트 결과

## 4.1 매치 순위에 영향을 주는 요인

![image](https://user-images.githubusercontent.com/73567364/228254597-8a42fb03-36c8-4dd0-a23b-163a7efe8904.png)

```{r}
높은 순위를 차지하기 위해서 유저들이 취하는 방법에는 크게 2가지가 있음. 

1. 교전을 통해서 적을 제거하는 방법 
2. 교전을 피하면서 오래 살아남는 방법 

분석 결과, 높은 등수를 차지한 그룹은 교전을 피하는 그룹이 아니라 전투력이 높고 교전을 많이 진행한 그룹이었음을 확인할 수 있었음.
```

```
따라서, 매치 순위에 영향을 주는 요인은 그룹의 전투력이라고 할 수 있음.
```
## 4.2 Rank & MAE

```
Rank : 5 / 1528 (0.327%) 
MAE : 0.01836
```

![image](https://user-images.githubusercontent.com/73567364/228254810-c06e1ffc-2a5d-451c-b114-6b4f2f2876bd.png)

# 5. File directory
```
📂 Project
├── 📂 code
│    ├── Baseline.ipynb   # Baseline model
│    ├── EDA.ipynb   
│    ├── get_group_place_function.ipynb   # Function for getting group places
│    ├── postprocessing.ipynb   # Postprocessing predicted valuefrom continuous to discrete
│    └── LightGBM_final.ipynb   # Final model
├── 📂 dataset
│    ├── train_sample.csv   # train data sample
│    ├── test_sample.csv   # testdata sample
│    └── sampleSubmission_sample.csv   # submission file sample
└── 📂 final
     ├── report.pptx 
     ├── report.pdf 
     └── submission.csv # final submission file
```


