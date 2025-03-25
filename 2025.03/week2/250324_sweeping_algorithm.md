# TIL - 2025.03.24 (월요일)

## 📝 오늘 배운 것 (라인 스위핑 Sweeping Algorithm)

### 라인 스위핑

라인 스위핑(line Sweeping) 알고리즘은 **선 하나를 여러 가지 상황에서 움직이면서** 문제를 해결하는 방법

스위프트(빗자루)가 평면을 가로지르면서 이벤트를 처리하는 방식을 모방한 것으로 일반적으로 평면상의 선이나 구간과 관련된 문제를 해결하는 데 사용한다.

#### 사용 예시

- 선분 교차
- 겹치는 구간 찾기
- 최근접 점 쌍 찾기 등

#### 시간 복잡도

O(NlogN)의 시간 복잡도를 평균적으로 가진다.

### 스위핑 적용 과정

![alt text](<스크린샷 2025-03-24 오전 8.39.10.png>)
<center>이미지 출처 : https://blogshine.tistory.com/120</center>

스위핑 알고리즘을 적용하기 위해 살펴봐야할 부분은 다음과 같다.

1. 선들이 완전히 겹치는 경우
2. 선들이 일부 겹치는 경우
3. 선들이 겹치지 않는 경우

왼쪽 부터 움직이며 start, end 값을 변경해야 한다.

1. 선들이 완전히 겹치는 경우 : 비교하고 있는 선이 최초 설정한 선과 같은 시작점과 끝점을 가지고 있거나 그보다 작아 완전히 겹쳐진 상태에는 start와 end 값을 변경하지 않는다.
2. 선들이 일부 겹치는 경우 : 비교하고 있는 선이 최초 설정한 선과 비교했을 때 시작점이 포함이 되나 끝 점이 더 큰 경우 start는 유지하고 end 값을 더 큰 값으로 대체
3. 선들이 겹치지 않는 경우 : 최종 결과 값에 길이를 더해준 후 새로운 선이 나타난 것이니 start, end를 새로 초기화 한다.

```python
n = int(input())

lines = []
for _ in range(n):
    a, b = map(int, input().split())
    lines.append([a, b])
lines.sort(key=lambda x : x[0]) # 시작점으로 오름차순 정렬

start, end = lines[0][0], lines[0][1]
answer = 0 # 선들의 합
for i in range(1, n):
    if lines[i][0] <= end and lines[i][1] <= end: # 완전 겹치는 경우
        continue
    elif lines[i][0] <= end and lines[i][1] > end: # 약간 겹치는 경우
        end = lines[i][1]
    else: # 아예 안겹치는 경우
        answer += end - start
        start = lines[i][0]
        end = lines[i][1]
answer += end-start
print(answer)
```

## 💡 문제 해결

> 백준 10000 원 영역을 풀기 위해 찾다 보니 라인 스위핑이라는 키워드가 있어 이를 조사해봤다.

## 🔍 더 알아볼 것

<input type="checkbox"> 추가 문제 풀어보기

<input type="checkbox"> 10000 원 영역 풀기

## 🧐 느낀 점

알고리즘 문제 하나 풀기 위해 정말 여러 개념들이 포함되고 이 개념을 적절하게 사용하는 것이 매우 어렵다

## 📚 참고 자료

- [[백준/BOJ][Python] 2170번 선 긋기](https://velog.io/@dkan9634/%EB%B0%B1%EC%A4%80BOJPython-2170%EB%B2%88-%EC%84%A0-%EA%B8%8B%EA%B8%B0-wn9ag3vh)