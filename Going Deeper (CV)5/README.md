# AIFFEL Campus Online Code Peer Review
- 코더 : 김수진
- 리뷰어 : 김민규

# PR(Peer Review)
- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**

     >결과 분석을 깔끔하게 진행했습니다.

     | 평가문항                                                               | 상세기준                                                                                                               | 달성여부 |
     | ---------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | -------- |
     | 1. U-Net을 통한 세그멘테이션 작업이 정상적으로 진행되었는가?           | KITTI 데이터셋 구성, U-Net 모델 훈련, 결과물 시각화의 한 사이클이 정상 수행되어 세그멘테이션 결과 이미지를 제출하였다. |o          |
     | 2. U-Net++ 모델이 성공적으로 구현되었는가?                             | U-Net++ 모델을 스스로 구현하여 학습 진행 후 세그멘테이션 결과까지 정상 진행되었다.                                     |o          |
     | 3. U-Net과 U-Net++ 두 모델의 성능이 정량적/정성적으로 잘 비교되었는가? | U-Net++ 의 세그멘테이션 결과 사진과 IoU 계산치를 U-Net과 비교하여 우월함을 확인하였다.                                 |o          |

     - 1번 루브릭
     ![image](https://github.com/sujin7822/AIFFEL_QUEST/assets/68997408/f8bcfa9f-9072-4d0b-bd54-1c9014714585)
     - 2번 루브릭
     ![image](https://github.com/sujin7822/AIFFEL_QUEST/assets/68997408/699a1112-cfb0-4789-9164-40b18615ee6a)

     - 3번 루브릭
       - U-Net IoU  
         ![image](https://github.com/sujin7822/AIFFEL_QUEST/assets/68997408/29cb7f7a-a27d-4cb5-8d88-ce656aeffdea)
       - U-Net++ IoU  
         ![image](https://github.com/sujin7822/AIFFEL_QUEST/assets/68997408/7caa9308-3660-4b56-8c5c-41ca87c42c1a)

- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
     >코드마다 주석이 잘 붙어있어 이 코드가 어떤 코드인지 이해하기 쉽습니다.
     
- [ ]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” ”새로운 시도 또는 추가 실험을 수행”해봤나요?**

- [x]  **4. 회고를 잘 작성했나요?**
     >회고를 잘 작성했습니다.


       
- [x]  **5. 코드가 간결하고 효율적인가요?**
     >반복되는 부분이나 복잡한 부분은 함수로 정리해서 코드가 깔끔합니다.  