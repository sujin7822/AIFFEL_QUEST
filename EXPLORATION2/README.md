# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 김수진
- 리뷰어 : 김서연


# PRT(Peer Review Template)
- [X] **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
  - 문제를 잘 해결했다.
  - ![review](https://github.com/Seoyeon1129/AIFFEL_QUEST_sj/assets/112914475/84bef2c5-e92e-4a34-939f-d171f6b907a8)

- [X] **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
  - 주석으로 코드 설명이 잘 되어있다.
  - ```python
    def get_scores(models, train, y):
    df = {}
    for model in models:
        # 모델 이름 획득
        model_name = model.__class__.__name__
        # train, test 데이터셋 분리
        # random_state를 사용하여 고정하고 train과 test 셋의 비율은 8:2로 합니다.
        X_train, X_test, y_train, y_test = train_test_split(train, y, test_size=0.2, shuffle=True, random_state=34) 

        # 모델 학습
        model.fit(X_train, y_train)
        # 예측
        y_pred = model.predict(X_test)
        score_df = pd.DataFrame(df, index=['RMSE']).T.sort_values('RMSE', ascending=False)

        # 예측 결과의 rmse값 저장
        df[model_name] = rmse(y_pred, y_test)
    
        # data frame에 저장
        score_df = pd.DataFrame(df, index=['RMSE']).T.sort_values('RMSE', ascending=False)
    ```    
  - ```python
    #gridsearchcv 실행순서 : 모델 초기화, 학습시키기 -> 모든 파라미터 조합의 실험
    grid_model = GridSearchCV(model, param_grid=param_grid, \
                            scoring='neg_mean_squared_error', \
                            cv=5, verbose=1, n_jobs=1)
    
    grid_model.fit(train, y)
    ```
    

- [X] **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나”
”새로운 시도 또는 추가 실험을 수행”해봤나요?**
  - 노드에서 학습한 내용을 활용하여 추가적인 실험을 잘 수행했다.
  - <img width="388" alt="스크린샷 2023-09-27 오후 12 20 41" src="https://github.com/Seoyeon1129/AIFFEL_QUEST_sj/assets/112914475/2988faa5-fdc3-4c5e-82f4-a3a79f5e86fd">

  - <img width="860" alt="스크린샷 2023-09-27 오후 12 20 32" src="https://github.com/Seoyeon1129/AIFFEL_QUEST_sj/assets/112914475/cfdd8663-c34d-4990-83a8-d7ec3387b2c7">


- [X] **4. 회고를 잘 작성했나요?**
  - 배운 점과 아쉬운 점, 느낀 점이 잘 설명되어있다.
  - 전체 코드의 플로우를 설명하면 더 좋을 것 같다.

- [X] **5. 코드가 간결하고 효율적인가요?**
  - 중요 코드의 함수화가 잘 이루어져 있다.
  - ```python
    def my_GridSearch(model, train, y, param_grid, verbose=2, n_jobs=5):
      # GridSearchCV 모델로 초기화
      grid_model = GridSearchCV(model, param_grid=param_grid, scoring='neg_mean_squared_error', \
                                cv=5, verbose=verbose, n_jobs=n_jobs)
  
      # 모델 fitting
      grid_model.fit(train, y)
  
      # 결과값 저장
      params = grid_model.cv_results_['params']
      score = grid_model.cv_results_['mean_test_score']
  
      # 데이터 프레임 생성
      results = pd.DataFrame(params)
      results['score'] = score
  
      # RMSLE 값 계산 후 정렬
      results['RMSLE'] = np.sqrt(-1 * results['score'])
      results = results.sort_values('RMSLE')
  
      return results
    ```
  - ```python
    def save_submission(model, train, y, test, model_name, rmsle=None):
      model.fit(train, y)
      prediction = model.predict(test)
      prediction = np.expm1(prediction)
      data_dir = data_dir
      submission_path = join(data_dir, 'sample_submission.csv')
      submission = pd.read_csv(submission_path)
      submission['price'] = prediction
      submission_csv_path = 'submission_{}_RMSLE_{}.csv'.format(model_name, round(rmsle,3))
      submission.to_csv(submission_csv_path, index=False)
      print('{} saved!'.format(submission_csv_path))
    ```


# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
