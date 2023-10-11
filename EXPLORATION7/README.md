# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 김수진
- 리뷰어 : 서민성


# PRT(Peer Review Template)
- [ ]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 퀘스트 문제 요구조건 등을 지칭
        - 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부
        -  1. pix2pix 모델 학습을 위해 필요한 데이터셋을 적절히 구축하였다.
           - 데이터 분석 과정 및 한 가지 이상의 augmentation을 포함한 데이터셋 구축 과정이 체계적으로 제시되었다.
           - ![스크린샷 2023-10-11 오후 12 11 41](https://github.com/sujin7822/AIFFEL_QUEST/assets/138687269/34a26b25-2cf4-4639-b542-20db86e0deeb)
       - 2. pix2pix 모델을 구현하여 성공적으로 학습 과정을 진행하였다.
             - U-Net generator, discriminator 모델 구현이 완료되어 train_step의 output을 확인하고 개선하였다.
             - 네 완료하였습니다.
             - ![스크린샷 2023-10-11 오후 12 13 49](https://github.com/sujin7822/AIFFEL_QUEST/assets/138687269/d080975c-6408-4de1-968e-7b355253b92c)

        - 3. 학습 과정 및 테스트에 대한 시각화 결과를 제출하였다.
             - 10 epoch 이상의 학습을 진행한 후 최종 테스트 결과에서 진행한 epoch 수에 걸맞은 정도의 품질을 확인하였다.
             - 네 10번의 epochs가 돌아간 것을 확인했으며 이를 시각화하여 확인하였습니다.
             - ![스크린샷 2023-10-11 오후 12 16 08](https://github.com/sujin7822/AIFFEL_QUEST/assets/138687269/58209290-e4e7-4861-b263-abe3384b1f46)
    
- [ ]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
        -  네 작성되어있었습니다.
    - 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
    - epochs가 수행될때마다 checkpoint_callback을 통하여 실험결과 저장하고 이를 불러오는 코드입니다.
    - ```
      import tensorflow as tf

        # Model Checkpoint 콜백 정의
        checkpoint_path = "weight_path/weights-{epoch:02d}.h5"  # 가중치 파일 이름에 에폭 번호를 포함
        checkpoint_callback = tf.keras.callbacks.ModelCheckpoint(
            checkpoint_path, save_weights_only=True, save_best_only=False, period=1
        )
        
        EPOCHS = 10
        
        # 모델 생성
        generator = UNetGenerator()
        discriminator = Discriminator()
        
        # 모델 컴파일 및 훈련
        
        # 훈련 시 Model Checkpoint 콜백 사용
        history = model.fit(train_dataset, epochs=EPOCHS, callbacks=[checkpoint_callback])
        
        # 에폭이 종료된 후 가중치 불러오기 (예를 들어, 에폭 5의 가중치를 불러오려면)
        loaded_model = UNetGenerator()  # 모델 생성
        loaded_model.load_weights("weight_path/weights-05.h5")  # 원하는 에폭의 가중치 파일을 불러옴
      ```
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        - ![스크린샷 2023-10-11 오후 12 21 34](https://github.com/sujin7822/AIFFEL_QUEST/assets/138687269/4b554366-05ea-4239-bfa4-3b032ffcbc10)

        
- [ ]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
        - 100epochs를 추가적으로 실험하는 기록이있었습니다. 
    - 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        - 학습 모델을 저장하는 시도가 있었습니다.
        - ![스크린샷 2023-10-11 오후 12 21 34](https://github.com/sujin7822/AIFFEL_QUEST/assets/138687269/4a6657e0-1f74-4111-bbd5-82ba6ca095ce)

        
- [ ]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        - 회고에 배운점과 아쉬운점 느낀점을 기록하였습니다.
        - ![스크린샷 2023-10-11 오후 12 17 52](https://github.com/sujin7822/AIFFEL_QUEST/assets/138687269/e1963f1e-5576-466e-8d8b-c448f92bf63c)

        
- [ ]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
        - 준수하여 작성하였습니다.
    - 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
        - 네 모듈화가 가능한 부분은 함수화하여 작성하였습니다. 
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        - for 문을 활용하여 시각화를 진행하였습니다.
        - ![스크린샷 2023-10-11 오후 12 27 20](https://github.com/sujin7822/AIFFEL_QUEST/assets/138687269/a0b867c6-d3a4-4f6a-ad1a-f11ff228b13b)



# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
