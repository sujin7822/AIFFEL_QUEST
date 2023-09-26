<<<<<<< HEAD
Code Peer Review

# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 김수진
- 리뷰어 : 임정훈.


# PRT(Peer Review Template)
- [ ]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    네 Ex01, 02 모두 잘 첨부 되어 있습니다. 예측값과 실제 값이 유사하게 나왔습니다.
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 
    퀘스트 문제 요구조건 등을 지칭
        - 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부
        
        Ex01:  mse값이 3000이하로 나왔습니다
        prediction = model(X_test, W, b)
        mse = loss(X_test, W, b, y_test)
        2824.501093201547
        Ex02: rmse값이 150 이하로 나왔습니다     
        rmse = mean_squared_error(y_test, predictions, squared=False)
        rmse:  149.91495105433168
    
- [ ]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    네 Ex01,02 모두 잘 달려 있습니다.
    - 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
    Ex01은 자세히 적혀있는 반면, Ex02는 미흡합니다.
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
    주석을 보니 코드를 잘 이애하고 있다고 느껴집니다.
    
    def gradient(X, W, b, y):
    # N은 데이터 포인트의 개수
    N = len(y)
    
    # y_pred 준비
    y_pred = model(X, W, b)
    
    # 공식에 맞게 gradient 계산
    dW = 1/N * 2 * X.T.dot(y_pred - y)
        
    # b의 gradient 계산
    db = 2 * (y_pred - y).mean()
    return dW, db
        
        
        
- [ ]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    문제 원인 및 해결 과정은 적혀 있지 않습니다
    - 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
    문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도는 없습니다.
        
- [ ]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    네 배운점과 아쉬운점, 느낀점을 간략히 잘 적었습니다.
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
    전체 체 코드 실행 플로우에 대한 부분은 작성되어 있지 않습니다
        
        
- [ ]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    네 파이썬 스타일 가이드를 잘 준수하고 적었습니다.
    - 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
    Ex01에서 for i in range(10)이 부분이 하드 코딩 되어 있습니다. 함수로 만들어야 하는 부분은 다 잘 구성하였습니다.
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
    네 잘 작성되어 있습니다
        
    def model(X, W, b):
    predictions = 0
    for i in range(10):
        predictions += X[:, i] * W[i]
    predictions += b
    return predictions
    def MSE(a, b):
          mse = ((a - b) ** 2).mean()  # 두 값의 차이의 제곱의 평균
          return mse
    def loss(x, w, b, y):
        predictions = model(x, w, b)
        L = MSE(predictions, y)
        return L


# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
Ex01
df_x와 df_y는 이미 numpy 배열이여서 변환은 불필요하다.->
df_X = np.array(df_x)
df_y = np.array(df_y)
삭제했습니다

for i in range(10) 하드코딩
num_features = X.shape[1]
for i in range(num_features):
으로 대체했습니다.

Ex02
train['minute'] = train['datetime'].dt.minute
train['second'] = train['datetime'].dt.second
이 두 부분은 모두 0의 값을 가지므로 불필요하다

import matplotlib.pyplot as plt두번 선언되어서 하나 제거했습니다.

Ex01,02
변수 명이 일관되지 않아서 일관성 유지를 하면 좋을 것 같습니다.

=======

>>>>>>> 77f9d91ae26b3400b553aa21b344f234d2e43a99
