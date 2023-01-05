# 코딩테스트를 위한 파이썬 문법

## 01. 자료형

---

### 수 자료형
- 정수형
    - 양의 정수, 음의 정수, 0
    ```python
    a = 1000
    b = -7
    c = 0
    ```

- 실수형
    - 소수점 아래의 데이터를 포함
    - 소수부가 0이거나 정수부가 0이면 0 생략 가능
    ```python
    a = 157.93
    b = 5. #5.0 소수부가 0일 때 0 생략
    c = -.7 #-0.7 정수부가 0일 때 0 생략
    ```

    - e나 E를 이용하여 지수 표현 가능
    - 유효숫자e지수 = 유효숫자x10^지수
    ```python
    a = 1e9 #10^9표현
    b = 75.25e1 #752.5
    c = 3954e-3 #3.954
    ```

    - 반올림
    ```python
    a = 0.3+0.6
    print(a) #0.89999999999 출력
    print(round(a, 4)) #0.9 출력
    ```

- 수 자료형의 연산
    - +, -, *, **(거듭제곱), /(실수형), //(정수형), %(나머지)
    ```python
    print(7/3) #2.333333333335
    print(7//3) #2
    print(7%3) #1
    print(2**3) #8
    ```

---
### 리스트 자료형
- 리스트 만들기
    - 대괄호([]) 안에 원소를 넣어 초기화, 쉼표로 구분
    - 인덱스는 0부터 시작
    - 빈 리스트 선언 : list() / []
    ```python
    a = [1, 2, 3, 4, 5]
    print(a[2]) #3이 출력

    a = list() #초기화 방법 1
    a = [] #초기화 방법 2
    ```

- 리스트 인덱싱과 슬라이싱
    - 인덱싱 : 리스트의 특정 원소에 접근
    - 슬라이싱 : 연속적인 위치의 원소(시작:끝)
    ```python
    a = [1, 2, 3, 4, 5]
    print(a[2]) #앞에서 3번째 원소
    print(a[-1]) #뒤에서 1번째 원소
    a[-2] = 6 #뒤에서 2번째 원소 4를 6으로 변경

    print(a[1:3]) #1번인덱스~2번인덱스 즉, 2, 3 출력
    ```

- 리스트 컴프리헨션
    - 리스트 초기화하는 방법
    - 한 줄의 소스코드로 리스트를 세팅할 수 있음
    ```python
    a = [i for i in range(20) if i%2 == 1] #홀수만 포함하는 리스트
    b = [i*i for i in range(1, 10)] #1부터 9까지 수의 제곱 값을 포함하는 리스트

    #2차원 리스트
    n = 3
    m = 4
    c = [[0] * m for _ in range(n)] #[[0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
    ```
    -> 언더바(_)의 역할 : 단순 반복에 사용

- 리스트 관련 기타 메서드
    - append() : 리스트에 원소를 하나 삽입할 떄 사용
    - sort() : 정렬 기능. 오름차순으로 정렬
    - sort(reverse=True) : 정렬 기능. 내림차순으로 정렬
    - reverse() : 원소의 순서 뒤집어 놓음
    - insert(위치 인덱스, 삽입할 값) : 인덱스 위치에 원소 삽입
    - count() : 특정 값의 개수
    - remove() : 특정 값을 갖는 원소 제거, 여러 개면 하나만 제거 
    ```python
    a = [1, 4, 3]
    a.append(2) #[1, 4, 3, 2]
    a.sort() #[1, 2, 3, 4]
    a.sort(reverse=True) #[4, 3, 2, 1]
    a.reverse() #[1, 2, 3, 4]
    a.insert(2, 3) #[1, 2, 3, 3, 4]
    a.count(3) #2
    a.remove(1) #[2, 3, 3, 4]
    ```
    -> reverse, insert, remove는 시간복잡도가 O(N)으로 오래 걸림   
    -> 아래와 같은 방식을 이용할 것
    ```python
    a = [1, 2, 3, 4, 5, 5, 5]
    remove_set = [3, 5]

    result = [i for i in a is i not in remove_set] #a에서 remove_set에 없는 원소만을 갖는 리스트
    print(result) #[1, 2, 4]
    ```

---

### **문자열**

- 문자열 반복

    ```python
    hi = '안녕'*5
    ```

- 문자열 포매팅

    % 이용

    ```python
    height = 172.5
    a = '키는 %.2f입니다.' % height

    print(a)
    ```

    str.format 이용

    → 자료형 몰라도 가능

    ```python
    test = 'Hello {}'.format('Bob')

    print(test)
    ```

    자릿수 맞추기

    ```python
    year = 2020
    month = 3
    day = 5

    a = '%d-%02d-%02d' % (year, month, day)
    print(a)
    ```

    역순 출력

    ```python
    #방법 1
    	def strReverse1(string):
        return string[::-1]
    		#튜플, 리스트 전부 적용 가능

    #방법 2
    		def strReverse(string):
        return reversed(string)
        
    in_string = input('문자열을 입력하세요: ')
    result = strReverse(in_string)
    print(''.join(result))
    ```

    비교

    ```python
    #완전일치
    if str1 == str2:

    #부분일치
    if str1 in str2:

    #전방일치
    if str1.startswith(str2):

    #후방일치
    if str1.endswith(str2):
    ```

---

### 화면출력

- separator

    : 각 항목사이의 문자 정의

    ```python
    year = 2020
    month = 3
    day = 5

    print(year, month, day, sep='/')
    ```

- end

    : 출력 내용의 마지막에 들어갈 문자열

    ```python
    a = '안녕하세용'
    print(a, end='')
    ```

---

### 입력

- input()

    ```python
    name = input('이름을 입력하세요: ')

    print('%s님 반갑습니다.' % name)
    ```

---

### 조건문

- 조건부 표현식

    ```python
    score = 85
    result = "Success" if score>=80 else "Fail"
    ```

    ```python
    a = [1,2,3,4,5,5,5]
    remove_set = {3,5}

    result = [i for i in a if i not in remove_set]
    ```

---

### 반복문

1. `range(종료값)`

    > 0 ~ 종료값-1의 정수 범위(1씩 증가)의 값을 가집니다.

2. `range(시작값, 종료값)`

    > 시작값에서 종료값-1의 정수 범위(1씩 증가)의 값을 가집니다.

3. `range(시작값, 종료값, 증가값)`

    > 시작값 ~ 종료값~1의 정수 범위를 갖는데, 각 정수 사이의 간격은 증가값에 의해 결정됩니다.

4. `range(시작값, 종료값, 감소값)`

    > 감소값, 즉 음수의 값을 가지는 경우 범위는 시작값 ~ 종료값+1 이 됩니다.

---

### 리스트

- **`index(a)`**

    : 리스트 요소 a의 인덱스 값 return

    ```python
    #뒤에서 첫번째
    print(a[-1])

    #뒤에서 세번째 
    print(a[-3])
    ```

- **`pop(x)`**

    : x번째 인덱스의 요소를 리스트에서 삭제

- `insert(x,y)`

    : x번째에 y추가

- **`remove(a)`**

    :  리스트에서 값 a를 가진 요소 삭제

    → 여러개면 하나만

- `count(a)`

    : 리스트에서 값 a를 가지는 원소 개수 

    ```python
    a = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
    x = a.index(30)
    print(x)

    a.pop(x)     # del a[x]와 동일
    print(a)

    a.remove(90)
    print(a)

    a.clear()
    print(a)
    ```

- `sort()`

    : 리스트의 오름차순 정렬

    → 내림차순은 reverse=True 이용 

    ```python
    list2 = [-7, 1, 5, 8, 3, 9, 11, 13]
    list2.sort()
    print(list2)

    list2.sort(reverse=True)
    print(list2)
    ```

- `join()`

    : list to string

    ```python
    list2 = ['A', 'B', 'C']
    print(''.join(list2))
    ```

- List comprehension

    ```python
    array = [i for i in range(20) if i%2 == 1]

    #array=[]
    #for i in range(20):
        #if i%2 == 1:
            #array.append(i)
    ```

→ 리스트 컴프리헨션 이용해 2차원 리스트초기화

    ```python
    n=3
    m=4
    array = [[0]*m for _ in range(n)]
    ```

- _는 ?

    반복을 수행하되 반복을 위한 변수값을 무시할때

---

### 튜플

- 튜플과 리스트

    : 튜플은 소괄호() 사용, 요소의 수정/삭제 불가능

    → 리스트에 비해 공간효율적, 각 원소의 성질이 다를떄 주로 사용

- 삭제

    ```python
    #tuple1의 존재 자체를 완전히 삭제
    del tuple1
    ```

---

### 딕셔너리

- key와 value로 구성

    ```python
    members = {'name':'김우경', 'age':25, 'phone':'010-3787-3146'}

    #접근
    print(members['name'])
    ```

- 추가, 수정, 삭제 가능
- 관련 함수

    ```python
    key_list = data.keys()

    value_list = data.values()
    ```

- for문 활용

    ```python
    phones = {'갤럭시 노트8': 2017,  '갤럭시 S9': 2018, '갤럭시 노트10': 2019, '갤럭시 S20': 2020}
    print(phones)

    for phone in phones :
        print('%s => %s' % (phone, phones[phone]))

    print(len(phones))
    ```

- 정렬

    ```python
    fruits = { 'apple': 2, 'banana' : 1, 'pear' : 2, 'melon' : 0, 'plum' : 1}

    #key 기준 정렬
    res = sorted(fruits)
    print(res)

    #value 기준 정렬
    res = sorted(fruits, key=lambda k : fruits[k])
    print(res)
    ```

---

### 집합

- 특징

    : 중복 허용x, 순서 x

- 초기화

    ```python
    data = set([1,2,3,4,5])

    data = {1,2,3,4,5}
    ```

- 연산

    : 합집합, 교집합, 차집합 제공

    ```python
    a = set([1,2,3,4,5])
    b = set([3,4,5,6,7])

    print(a|b)
    print(a&b)
    print(a-b)
    ```

- 관련 함수

    ```python
    data = set([1,2,3])

    data.add(4)
    #원소 여러개 추가
    data.update([5,6])
    #특정값 갖는 원소 삭제
    data.remove(3)
    ```

---

### 함수

- n개의 매개변수

    : 매개변수의 개수 정하지 x

    ```python
    def average(*scores) :
        sum = 0
        for i in range(len(scores)) :
            sum += scores[i]
        
        avg = sum/len(scores)
        print('%d과목의 평균 : %.2f' % (len(scores), avg))

    average(80, 90, 100)
    average(75, 80, 94, 78)
    average(80, 73, 76, 86,82)
    ```

- 할당에 의한 호출(Call by Assignment)

    : 함수 호출 시 전달되는 값이나 변수의 데이터 형에 따라 자동으로 call by value나 call by reference 선택

    ```python
    #call by value
    def func(x) :
        x = 100
        print('func() : x = ', x, ', id =', id(x))

    x = 10
    print('메인 : x = ', x, ', id =',id(x))
    func(x)
    print('메인 : x = ', x, ', id =', id(x))
    ```

    - id()

    ```python
    # call by reference
    def func(x) :
        x[0] = 100
        print('func() : x = ', x, ', id =', id(x))

    x = [1,2,3]
    print('메인 : x = ', x, ', id =', id(x))
    func(x)
    print('메인 : x = ', x, ', id =', id(x))
    ```

- 람다 함수

    : `**lambda 매개변수 1, 매개변수2, ... : 수식**`

    ```python
    f = lambda x, y, z: x+y+z
    print(f(10, 20, 30))

    def mul(n) :
        return lambda x : x * n

    g = mul(3)
    h = mul(5)

    print(g(10))
    print(h(10))
    ```

- 전역변수

    : global 이용해 선언

- 파일 쓰기

    ```python
    #파일객체 = open(파일명, 파일모드, 인코딩)
    file = open('sample.txt', 'w', encoding='utf8')
    ```

    - 파일모드

---

### 파이썬의 객체지향

    ```python
    class  Member:
        def __init__(self, name, age) :
            self.name = name
            self.age = age

        def showMember(self) :
            print('이름 : %s' % self.name)
            print('나이 : %d' % self.age)
            
    mem1 = Member('홍지수', 24)
    mem1.showMember()
    mem2 = Member('안지영', 20)
    mem2.showMember()
    ```

- 상속

    ```python
    class Animal:
        def __init__(self, name):
            self.name = name

        def printName(self):
            print(self.name)
            
    class Dog(Animal):
        def __init__(self, name, sound):
            super().__init__(name)
            self.sound = sound
            
        def printSound(self):
            print(self.sound)

    dog1 = Dog('행복이','멍멍~~~')
    dog1.printName()
    dog1.printSound()
    ```