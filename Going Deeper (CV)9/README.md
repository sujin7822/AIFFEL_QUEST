# AIFFEL Campus Online Code Peer Review
- 코더 : 김수진
- 리뷰어 : 이동희

# PR(Peer Review)
- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**    
> 1. 잠재적 표현의 변화가 모델 출력에 미치는 영향을 관찰하였는가? -> O
> 2. Stable diffusion 모델의 dreambooth 미세조정을 실습하였는가? -> O
> 3. 나만의 취향이 담긴 생성 이미지를 만들어보았는가? -> O

- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**  

        
- [x]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나”   
”새로운 시도 또는 추가 실험을 수행”해봤나요?**  
```py
prompt = "sks starbucks smile"
image = pipeline(prompt, num_inference_steps=50, guidance_scale=7.5).images[0]

image.save("dog-graduate.png")
image
```
        
- [x]  **4. 회고를 잘 작성했나요?**    
> 회고
> 이번 노드는 한 번 읽어보며 실행하는 느낌으로 진행했다.
> AI가 직접 이미지를 만들 수 있다는게 신기했다.
    
        
- [x]  **5. 코드가 간결하고 효율적인가요?**  
