# TIL - 2025.03.17 (월요일)

## 📝 오늘 배운 것 (비트마스크)

### 비트마스크(BitMask)?
- 비트마스크는 이진수를 사용하는 컴퓨터의 연산 방식을 이용하여, 정수의 이진수 표현을 자료 구조로 쓰는 기법을 말한다.
- 이진수는 0 또는 1을 이용하므로 하나의 비트가 표현할 수 ㅣㅆ는 경우는 두 가지이다.
- 보통 어떤 비트가 1이면 "켜져 있다"라고 말하며, 0이면 "꺼져 있다"라고 말한다.

### 비트마스크의 장점

1. 수행 시간이 빠르다.
비트마스크 연산은 bit 연산이기 때문에 O(1)에 구현되는 것이 많다. 따라서 다른 자료구조를 이용하는 것보다 훨씬 빠르게 동작한다.
단. 비트마스크를 이용하는 경우에는 비트의 개수만큼 원소를 다룰 수 있기 때문에 연산 횟수가 적은 경우에는 속도에 큰 차이가 없지만, 연산 횟수가 늘어날수록 차이가 커지게 된다.
2. 코드가 짧다.
다양한 집합 연산들을 비트연산자로 한 줄로 작성할 수 있기 때문에 반복무느 조건문 등을 이용한 코드보다 훨씬 간결한 코드를 작성할 수 있다.
3. 메모리 사용량이 더 적다.
종종 문제 중 메모리 초과가 나는 문제가 있는데 이 경우 비트마스크를 이용하면 해결되는 경우가 있다.

### 비트 연산자

비트마스크를 이용하기 위해 비트 연산자를 사용한다.

1. AND 연산
두 정수 변수 a와 b를 통해서 c를 생성한다고 가정하면, a와 b를 한 bit씩 비교하면서 해당 비트가 둘다 켜져 있는 경우에만 c의 해당 비트를 켠다. --> `&`

2. OR연산
AND 연산과 같은 방식으로, 해당 비트가 둘 중 하나라도 켜져 있는 경우에 c의 해당 비트를 켠다. --> `|` 

3. XOR연산
해당 비트가 둘중 하나만 켜저 있는 경우에 c의 해당 비트를 켠다. --> `^`

4. NOT연산
정수 하나를 입력받아서 켜져 있는 비트는 끄고, 켜져 있는 비트는 켠 결과를 반환 --> `~`

5. 시프트(Shift)연산
시프트 연산자는 정수 a의 비트들을 왼쪽 또는 오른쪽으로 원하는 만큼 움직인다. 움직이고 나서 빈자리는 0으로 채워지게 된다. 예를 들어 13(1101)을 오른쪽으로 1bit 움직인다고 하면 6(0110)이 되는 것이다. --> `<<, >>`

### 비트마스크를 이용한 집합 구현

비트마스크를 이용한 집합 구현은 가장 대표적인 사례이다. **하나의 bit가 하나의 원소**를 의미하게 된다. bit가 켜져 있으면 해당 원소가 집합에 포함되어 있다는 의미이고 꺼져 있다면 포함되어 있지 않다는 의미이다.

| 연산                       | 사용 예시                                                                                                                                 |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 공집합과 꽉 찬 집합 구하기 | A = 0; / A = (1 << 10) - 1;                                                                                                               |
| 원소 추가                  | A \|= (1 << k);                                                                                                                           |
| 원소 삭제                  | A &= ~(1 << k);                                                                                                                           |
| 원소의 포함 여부 확인      | if(A & (1 << k))                                                                                                                          |
| 원소의 토글(toggle)        | A ^= (1 << k);                                                                                                                            |
| 두 집합에 대해서 연산      | A \| B       → A와 B의 합집합 
|       |A & B     → A와 B의 교집합 
|       |A & (~B) → A에서 B를 뺀 차집합 
|       |A ^ B     → A와 B중 하나에만 포함된 원소들의 집합 |
| 집합의 크기 구하기         | int bitCount(int A){   if(A == 0) return 0;   return A%2 + bitCount(A / 2); }                                                             |
| 최소 원소 찾기             | int first = A & (-A);                                                                                                                     |
| 최소 원소 지우기           | A &= (A - 1);                                                                                                                             |
| 모든 부분 집합 순회하기    | for (int subset = A ; subset ; subset = ((subset - 1) & A)){ }                                                                            |

1. 공잡합과 꽉 찬 집합 구하기
- 기본적으로 공잡합은 모든 비트가 꺼진 상황임으로 0이 공집합을 표현한다. 반대로 꽉찬 집합은 이는 (1<<10) -1 과 동일하다. 1<<10 은 10000000000(2)으로 1을 빼면 10개의 비트가 모두 켜진 수를 얻을 수 있다.

2. 원소 추가


## 💡 문제 해결

> 오늘 해결한 문제나 어려웠던 부분을 기록합니다.

## 🔍 더 알아볼 것

- [ ] 항목 1
- [ ] 항목 2

## 🧐 느낀 점

오늘 배운 내용에 대한 개인적인 생각이나 느낌을 기록합니다.

## 📚 참고 자료

- [제목](링크)
