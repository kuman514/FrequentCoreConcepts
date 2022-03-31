## JavaScript

- 호이스팅
  - 같은 스코프 내에서 선언부 위에서도 참조를 할 수 있게 하는 JavaScript의 특성
  - var와 function은 undefined로 호이스팅되고, let과 const는 호이스팅되지 않는다
- 원형 (Prototype)
  - 객체의 원형
  - .__proto__를 통해 접근할 수 있음
  - 물론 .__proto__의 .__proto__로도 거듭해서 올라갈 수 있음
  - 모든 객체의 조상은 object (object의 프로토타입은 null)
- 화살표 함수와 function 키워드의 함수
  - function 키워드로 선언된 함수
    - function functionName (...) {...}의 형태로 선언된 함수
    - this가 정해지는 기준
      1. new functionName(...)
      2. .call(thisArg, ...), .apply(thisArg, [...]), .bind(thisArg)
      3. 객체 멤버로써의 호출
      4. 일반적인 호출
      5. 여러 기준을 만족하는 경우, 먼저 언급된 기준을 우선으로 한다
  - 화살표 함수
    - (...) => {...}의 형태로 선언된 함수
    - 이때, 이 함수의 this는 무조건 렉시컬 스코프에 의해 정해진 상위 스코프에 해당하는 this
- 클로저
  - 함수에 의해 return된 함수 중, 함수 외부에서 접근하지 못하는, 함수 내부의 변수에 접근할 수 있게 해 주는 함수
- 비동기 함수
  - Promise
    - 비동기 처리를, .then()을 통해 순차적으로, 또는 병렬로 처리하기 수월하도록 만들어진 패턴
    - 예외 처리는 .catch(error)로 진행한다
  - async와 await
    - Promise 패턴을 기반으로 조금 더 간결하게 만든 구문
    - 비동기 함수는 함수 앞에 async를 붙여서 만들면 되며
    - 비동기 처리를 순차적으로 진행시키고 싶을 경우 await를 통해 기다리도록 만들면 된다
    - try {...} catch (error) {...} 구문을 통해 예외 처리를 할 수 있다
