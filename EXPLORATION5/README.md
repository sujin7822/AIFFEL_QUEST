# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 김수진
- 리뷰어 : MyungJun Lee


**루브릭**
1. 인물모드 사진을 성공적으로 제작하였다.[X]
> 아웃포커싱 효과가 적용된 인물모드 사진과 동물 사진, 배경전환 크로마키사진을 각각 1장 이상 성공적으로 제작하였다.
2. 제작한 인물모드 사진들에서 나타나는 문제점을 정확히 지적하였다.[X]
> 인물사진에서 발생한 문제점을 정확히 지적한 사진을 제출하였다.
3. 인물모드 사진의 문제점을 개선할 수 있는 솔루션을 적절히 제시하였다.[X]
>semantic segmentation mask의 오류를 보완할 수 있는 좋은 솔루션을 이유와 함께 제시하였다.

_해결방안_
경계 부드럽게 만들기
배경 감지 및 교체
인물-배경 일치 향상
사용자 피드백 반영
모델 업데이트

# PRT(Peer Review Template)
- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - Final codes are submitted well
    - Achive 3 rubrics
    
- [X]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - There is no annotation but easy to understand
  ```python
  height, width, _ = img_orig1.shape
  img_orig = cv2.resize(img_orig, (width, height))
  plt.imshow(cv2.cvtColor(img_orig, cv2.COLOR_BGR2RGB))
  print(img_orig.shape)
  plt.show()```

- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” ”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    <img width="693" alt="image" src="https://github.com/Chancecatch1/AIFFEL_QUEST_SJ/assets/129345591/9b6a4a11-8fe6-45ee-adb2-671d5ecbd5dc">
    <img width="800" alt="image" src="https://github.com/Chancecatch1/AIFFEL_QUEST_SJ/assets/129345591/dced0d58-9a49-471c-88b5-f87ffcd1cab3">
    - Find many points that need to be fixed

- [X]  **4. 회고를 잘 작성했나요?**
    <img width="528" alt="image" src="https://github.com/Chancecatch1/AIFFEL_QUEST_SJ/assets/129345591/cf3491ec-91ce-4930-9a03-82ca53350aa9">

        
- [X]  **5. 코드가 간결하고 효율적인가요?**
    - Codes are simple and efficient


# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
