# E25_speech_recognition

# 결론

## 학습 결과 

- ***Spectogram 2차원 데이터로 Conv2D Skip Connection Model로 돌렸을 때는***
    - ***Valication accuracy는 97.96%로 가장 좋았고***
    - ***Valicatino loss는 0.078로 가장 낮았다.***
- ***Wave 1차원 데이터를 Con1D 모델로 돌렸을 때는***
    - ***Skip Connection Model 성능이 Base Model보다 0.9285% 높게 나왔다.*** 
- ***Spectorgram 2차원 데이터를 Con2D 모델로 돌렸을 때에도***
    - ***Skip Connection Model 성능이 Base Model보다 0.16% 높게 나왔다.*** 
- ***Spectorgram 2차원 데이터를 Con1D 모델로 돌렸을 때에는***
    - ***Skip Connection Model 성능이 Base Model보다 오히려 0.46% 낮게 나왔다.*** 


### (1) 1차원 Wave 데이터 셋 - (50620, 8000)

- npz 파일로 이뤄진 데이터이며, 각각 데이터는 "wav_vals", "label_vals"로 저장되어 있음
- 1초 길이의 오디오 음성 데이터 50620개, 각각 8000개의 샘플 데이터를 가짐
- ***Wave data shape: (50620, 8000)***

### (1-1) Wave Classification 첫번째 모델 구현 - (50620, 8000)

- Audio 데이터는 1차원 데이터이기 때문에 데이터 형식에 맞도록 모델 구성함
- Conv1D layer를 이용: Conv, batch norm, dropout, dense layer 등을 이용해 모델 구성
- ***Wav base model (Conv1D) : (8000, 1) 학습결과***
  - loss value: ***0.235***
  - accuracy value: ***93.6389%***

![image](Wave1-1.png)

### (1-2) Wave Classification 두번째 모델 구현 - (50620, 8000)

- Audio 데이터는 1차원 데이터이기 때문에 데이터 형식에 맞도록 모델 구성함
- 위의 Conv1D layer를 이용하지만 Skip Connection을 추가해서 모델을 구성함
- ***Wav skip connection model (Conv1D) : (8000, 1) 학습결과***
  - loss value: ***0.227***
  - accuracy value: ***94.5674%***
  
![image](Wave1-2.png)

### (2) 2차원 Spectogram 데이터 셋 - (45553, 130, 126, 1)

- 1차원의 Waveform 데이터가 2차원의 Spectrogram 데이터로 변환함
- 1차원의 1초 8000개의 샘플 데이터가 2차원 (130, 126) 샘플데이터로 변환됨
- ***Spectogram data shape: (45553, 130, 126, 1)***

### (2-1) Spectogram Classification Conv2D 모델 구현 - (45553, 130, 126, 1)

- Spectogram Audio 데이터는 2차원 데이터이기 때문에 데이터 형식에 맞도록 모델 구성함
- Conv1D layer를 이용: Conv, batch norm, dropout, dense layer 등을 이용해 모델 구성
- ***Spectogram base model (Conv2D) : (130, 126, 1) 학습결과***
  - Best Validation Loss : ***0.082***
  - Best Validation Accuracy : ***97.8%***

![image](Specto2-1.png)

### (2-2) Spectogram Classification Conv2D Skip Connection 모델 구현 - (45553, 130, 126, 1)

- Spectogram Audio 데이터는 2차원 데이터이기 때문에 데이터 형식에 맞도록 모델 구성함
- 위의 Conv1D layer를 이용하지만 Skip Connection을 추가해서 모델을 구성함
- ***Spectogram skip connection model (Conv2D) : (130, 126, 1) 학습결과***
  - Best Validation Loss : ***0.078***
  - Best Validation Accuracy : ***97.96%***
  
![image](Specto2-2.png)

### (3) 2차원 Spectogram 데이터 셋 - (45553, 130, 126)
- 1차원의 Waveform 데이터가 2차원의 Spectrogram 데이터로 변환함
- 1차원의 1초 8000개의 샘플 데이터가 2차원 (130, 126) 샘플데이터로 변환됨
- ***Spectogram data shape: (45553, 130, 126)***

### (3-1) Spectogram Classification Conv1D 모델 구현 - (45553, 130, 126)

- Spectogram Audio 데이터는 2차원 데이터이기 때문에 데이터 형식에 맞도록 모델 구성함
- Conv1D layer를 이용: Conv, batch norm, dropout, dense layer 등을 이용해 모델 구성
- ***Spectogram base model (Conv1D) : (130, 126) 학습결과***
  - Best Validation Loss : ***0.1782***
  - Best Validation Accuracy : ***95.19%***

![image](Specto3-1.png)

### (3-2) Spectogram Classification Conv1D Skip Connection 모델 구현 - (45553, 130, 126)

- Spectogram Audio 데이터는 2차원 데이터이기 때문에 데이터 형식에 맞도록 모델 구성함
- 위의 Conv1D layer를 이용하지만 Skip Connection을 추가해서 모델을 구성함
- ***Spectogram skip connection model (Conv1D) : (130, 126) 학습결과***
  - Best Validation Loss : ***0.1882***
  - Best Validation Accuracy : ***94.73%***
  
![image](Specto3-1.png)
