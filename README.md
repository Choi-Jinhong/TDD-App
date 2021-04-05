## 따라하며 배우는 TDD 개발
inflearn에서 강의 하는 '따라하며 배우는 TDD 개발'을 보고 정리한 내용들과 소스코드

<br/>

## 단위 테스트
### 단위(Unit) 테스트란?
- 단위 테스트는 개발자가 수행하고 자신이 개발한 코드 단위(일명 모둘, 구성요소)를 테스트하는 방법
- 소스코드의 **개별 단위**를 테스트하여 사용할 준비가 되었는지 확인하는 테스트 방법

### 단위 테스트의 장점
개발 라이프 사이클의 초기 단계에서 버그가 식별되므로 버그 수정비용을 줄이는데 도움이 됨

### 단위 테스트의 조건
1. 독립적이여야 함(의존 X)
2. 격리되어야 함 -> Ajax, Axios, LocalStorage 등 테스트 대상이 의존하는 것을 다른 것으로 대체해야 함

### 단위 테스트를 하는 이유
1. 프로그램이 크거나, 메모리가 많이 들거나, 다른 리소스등이 필요하면 실행시켜보기 어렵기 때문
2. 자신의 코드가 정상적으로 작동하는 지 빠르게 알 수 있기 때문
3. 종속성이 있는 다른 클래스들에서 버그가 나는 것을 방지하기 위해

<br/>

## Jest
### Jest란?
- Facebook에 의해서 만들어진 테스팅 프레임워크
- 최소한의 설정으로 동작하며 TestCase를 만들어 코드가 잘 돌아가는 지 확인해 줌
- 단위 테스트를 위해 사용

### Jest 시작하기
1. Jest 라이브러리 설치
```
npm install jest --save-dev
``` 
2. Test 스크립트 변경
```
"test":"jest" // or jest--watchAll
```
3. 테스트 작성할 폴더 및 파일 기본 구조 생성
    ex) test/unit/{파일명}.test.js, test/integration/{파일명}.int.test.js

### Jest가 Test파일을 찾는 방법
- **{파일명}.test.js**, **{파일명}.spec.js**, **"tests"폴더 내의 있는 파일**을 대상으로 테스트를 진행

<br/>

## jest.fn()

### jest.fn()이란?
- Mock 함수를 생성하는 함수
- 단위 테스트를 작성할 때 해당 코드가 의존하는 부분을 가짜로 대체하는 일을 함
*Mock: 모의, 가짜, 흉내내는*

### 단위 테스트가 독립적이어야 하는 이유
- 의존적인 부분을 구현하기 까다로움
- 의존적인 부분의 상태에 따라 테스트하고자 하는 부분의 결과의 영향을 미침

### jest.fn()의 역할
- 생성한 가짜 함수에 어떤 일들이 발생하는지 알 수 있음
- 다른 코드들에 의해서 어떻게 호출되는 지를 기억해 내부적으로 어떻게 사용되는지 알 수 있음

### jset.fn() 생성 방법
1. Mock(가짜) 함수 생성
```
const mockFunction = jest.fn();
```
2. 해당 함수를 통해 인자를 넘겨도 호출가능
```
mockFunction();
mockFunction(hello);
```
3. 반환값을 알려줄 수도 있음
```
mockFunction.mockReturnValue("가짜 함수 반환");
```
4. 가짜 함수가 몇 번 호출되었고 어떤 인자가 넘어왔는지 검증 가능
```
mockFunciton('hello)
mockFunction()

expect(mockFunction).toBeCalledWith('hello')
expect(mockFunction).toBeCalledTimes(2)
```