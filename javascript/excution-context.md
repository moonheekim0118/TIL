# 실행컨텍스트란 무엇인가요?

자바스크립트 엔진이 코드를 실행하는데 필요한 환경을 제공하는 객체입니다. 여기서 환경은 코드 실행에 영향을 주는 조건 혹은 상태를 나타냅니다. 모든 소스코드는 런타임 실행에 앞서서, 준비과정 즉 평가 과정을 거치게 됩니다. 즉 엔진은 소스코드 평가와 소스코드 실행 과정으로 나누어져있습니다. 소스코드 평가과정에서 실행컨텍스트를 생성하게 됩니다. 여기서 정의된 변수나 함수의 식별자를 정의하고, 스코프에 등록합니다.
따라서 자바스크립트 파일이 열리는 순간 전역 컨텍스트가 콜스택에 담기게 됩니다. 전역 컨텍스트는, 전역 공간의 실행 컨텍스트 입니다.
이 후에는 함수를 실행 할 때 실행컨텍스트가 구성됩니다.

# 실행컨텍스트의 구조를 설명해보세요.

- 실행컨텍스트는 크게 변수 환경과 렉시컬 환경, 그리고 this binding 으로 나누어져있습니다. 그런데 변수환경은 생략하고 말씀드리겠습니다. 변수환경은 렉시컬 환경과 구조가 동일하지만 변수환경이 최초의 스냅샷을 저장하는 반면 렉시컬환경은 코드 진행상황에 따라 달라지기 때문입니다.

- 렉시컬 환경은 때때로 스코프를 벗어난 뒤에도 존재하므로 (클로저 현상), 스택이 아니라 힙에 저장됩니다.
  렉시컬 환경 (Lexical Environment) 란 식별자와 식별자에 바인딩 된 값, 그리고 상위 스코프에 대한 참조를 기록하는 자료구조로, 실행 컨텍스트를 구성하는 컴포넌트입니다.
  간단하게, 렉시컬 환경은 스코프와 식별자를 관리한다고 생각하면 됩니다.

## 렉시컬 환경의 구조

![](https://user-images.githubusercontent.com/61469664/190890520-24802b1b-d1be-4115-960b-02d4239bf29b.JPG)

### 환경 레코드 (Environment Record)

- 스코프에 포함된 식별자를 등록하고, 등록된 식별자에 바인딩 된 값을 관리합니다.

### 외부 렉시컬 환경에 대한 참조 (Outer Lexical Environment Reference)

- 상위 스코프를 가리킵니다.
- 상위 스코프란, 외부 렉시컬 환경,즉 해당 실행 컨텍스트를 생성한 소스코드를 포함하는 상위 코드의 렉시컬 환경을 말합니다.

## 호이스팅의 발생 과정

- 호이스팅은 현재 실행할 스코프 내 식별자 정보를 수집하는 과정에서 발생하는 현상입니다. 따라서 실행컨텍스트 내 렉시컬 환경이 구성될 때, 현재 실행컨텍스트 내에 있는 변수와 함수 선언을 모두 수집하여 식별자 정보로 등록하게 됩니다. 이렇게 실행컨텍스트에 스코프 내의 식별자 정보를 미리 수집하는 전처리 과정을 '호이스팅'이라고 합니다.

## 호이스팅이 왜 일어나는가?

자바스크립트 엔진의 두 가지 역할을 구분할 필요가 있습니다. '코드 평가'와 '코드 실행'입니다. 코드 평가 단계에서 실행할 코드에 대한 정보를 모두 수집합니다. 이 과정에서 자바스크립트 엔진은 모든 스코프(실행컨텍스트)를 탐색하며 각 스코프의 변수 객체에 여러 식별자를 수집합니다. 즉, 실행시점으로 넘어가기 전에 선언된 식별자에 대한 정보를 이미 수집해놓았기 때문에 실행시점에서 스코프의 어느 지점이든 관련도니 함수/변수를 참조할 수 있게 됩니다. 그래서 호이스팅 과정이 꼭 필요하게 됩니다.