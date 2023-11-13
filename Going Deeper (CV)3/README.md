# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 김수진
- 리뷰어 : 김민규


# PRT(Peer Review Template)
- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**

| 평가문항                                                         | 상세기준                                                                                                                                | 달성여부 |
| ---------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| 1. CAM을 얻기 위한 기본모델의 구성과 학습이 정상 진행되었는가?   | ResNet50 + GAP + DenseLayer 결합된 CAM 모델의 학습과정이 안정적으로 수렴하였다.                                                         | o         |
| 2. 분류근거를 설명 가능한 Class activation map을 얻을 수 있는가? | CAM 방식과 Grad-CAM 방식의 class activation map이 정상적으로 얻어지며, 시각화하였을 때 해당 object의 주요 특징 위치를 잘 반영한다.      | o         |
| 3. 인식결과의 시각화 및 성능 분석을 적절히 수행하였는가?         | CAM과 Grad-CAM 각각에 대해 원본이미지합성, 바운딩박스, IoU 계산 과정을 통해 CAM과 Grad-CAM의 object localization 성능이 비교분석되었다. | o         |

- CAM 결과   
![image](https://github.com/sujin7822/AIFFEL_QUEST/assets/68997408/25910479-5ec5-4f7b-9ca3-c89d56243c14)

- CAM vs Grad-CAM   
![image](https://github.com/sujin7822/AIFFEL_QUEST/assets/68997408/dfb93232-fe19-44aa-aede-69ad4b065b74)



---

- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**

- image histogram    
![image](https://github.com/sujin7822/AIFFEL_QUEST/assets/68997408/6c9e3a8a-08d5-49a9-a0ad-fe37d948502c)
![image](https://github.com/sujin7822/AIFFEL_QUEST/assets/68997408/1f310100-ae33-4405-9b80-c1255409ca63)


---

- [x]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
”새로운 시도 또는 추가 실험을 수행”해봤나요?**

- threshold 변화에 따른 boundingbox 변화     
![image](https://github.com/sujin7822/AIFFEL_QUEST/assets/68997408/e55056f9-e3af-45eb-b560-8ec0eeb52df9)



---
        
- [x]  **4. 회고를 잘 작성했나요?**
![image](https://github.com/sujin7822/AIFFEL_QUEST/assets/68997408/002d0b82-eda6-48bc-bd9f-1ef2d140ec2e)





---
        
- [x]  **5. 코드가 간결하고 효율적인가요?**

- 전체적으로 for문을 활용해 코드 중복을 방지함   
![image](https://github.com/sujin7822/AIFFEL_QUEST/assets/68997408/c6d29ce9-1744-4a2a-a8df-9764b385f876)






---

수고하셨습니다!!  
실험에 따라 모델 학습시 참고할만한 코드입니다.!
```python
# 사용하는 함수들 정의해놓기
import pandas as pd

# 모델이름에서 히스토리 추출하는 함수
def get_history_from_path(path):
    epoch = []
    loss = []
    accuracy = []
    val_loss = []
    val_accuracy = []
    paths = []

    for i in os.listdir(path):
        if '.h5' in i:
            result = i[4:-3].split('-')

            epoch.append(float(i[:2]))
            loss.append(float(result[0]))
            accuracy.append(float(result[1]))
            val_loss.append(float(result[2]))
            val_accuracy.append(float(result[3]))
            paths.append(i)

    history = pd.DataFrame()
    history['path'] = paths
    history['epoch'] = epoch
    history['loss'] = loss
    history['accuracy'] = accuracy
    history['val_loss'] = val_loss
    history['val_accuracy'] = val_accuracy

    history.sort_values(by='epoch', inplace=True)
    
    history.reset_index(inplace=True, drop=True)
    
    return history

import matplotlib.pyplot as plt

def plot_history(history):
    loss = history['loss']
    val_loss = history['val_loss']

    epochs = range(1, len(loss) + 1)
    fig = plt.figure(figsize=(12, 5))

    ax1 = fig.add_subplot(1, 2, 1)
    ax1.plot(epochs, loss, 'b-', label='train_loss')
    ax1.plot(epochs, val_loss, 'r-', label='val_loss')
    ax1.set_title('Train and Validation Loss')
    ax1.set_xlabel('Epochs')
    ax1.set_ylabel('Loss')
    ax1.grid()
    ax1.legend()

    accuracy = history['accuracy']
    val_accuracy = history['val_accuracy']

    ax2 = fig.add_subplot(1, 2, 2)
    ax2.plot(epochs, accuracy, 'b-', label='train_accuracy')
    ax2.plot(epochs, val_accuracy, 'r-', label='val_accuracy')
    ax2.set_title('Train and Validation Accuracy')
    ax2.set_xlabel('Epochs')
    ax2.set_ylabel('Accuracy')
    ax2.grid()
    ax2.legend()

    plt.show()
    
from keras.callbacks import Callback
import os

class SaveModelEveryEpoch(Callback):
    def __init__(self, save_path, first_epoch=1):
        super(SaveModelEveryEpoch, self).__init__()
        self.save_path = save_path  # Path where you want to save the models
        self.first_epoch = first_epoch
        
    def on_epoch_end(self, epoch, logs=None):
        file_name = "{}--{:.4f}-{:.4f}-{:.4f}-{:.4f}.h5".format(self.first_epoch + epoch,
                                                                logs['loss'],
                                                                logs['accuracy'],
                                                                logs['val_loss'],
                                                                logs['val_accuracy'])
        model_save_path = os.path.join(self.save_path, file_name)
        
        self.model.save(model_save_path)
#         print(f'Model saved to {model_save_path}')
        
    def get_config(self):
        config = super(SaveModelEveryEpoch, self).get_config()
        config.update({'save_path': self.save_path, 'first_epoch': self.first_epoch})
        return config



```
