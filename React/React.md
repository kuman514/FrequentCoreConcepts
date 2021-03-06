## React

- Virtual DOM
    - DOM 트리를 메모리 상에서 구현한 React의 요소
    - 직접 DOM을 갱신하는 것과는 무슨 차이
        - 직접 DOM 갱신
            - 기존 프레임워크는 조금만 변경되어도 모든 DOM을 재렌더링하는 등, 불필요한 DOM까지 전부 갱신시켜 비효율적인 성능을 보였다 (예: jQuery)
        - Virtual DOM의 경우
            - 하지만 Virtual DOM을 사용하면 변경에 영향을 받는 컴포넌트들에 대한 목록을 정리하여 그에 해당하는 DOM들만 갱신하면 되므로 더욱 효율적이다
- 클래스 컴포넌트의 생명 주기
    1. constructor
        - 컴포넌트가 마운트되기 전에 호출
    2. render
        - 데이터가 변경되어 새 화면을 그려야 할 때 호출
    3. componentDidMount
        - render 함수가 JSX를 화면에 그린 이후
    4. componentDidUpdate
        - 컴포넌트가 실제 화면에 출력된 이후
    5. componentWillUnmount
        - 컴포넌트 소멸 직전에 호출
- 함수형 컴포넌트의 생명 주기
    1. componentDidMount → useEffect((...) => {...}, [])
        - 컴포넌트가 마운트된 이후 1회 실행
    2. componentDidUpdate → useEffect((...) => {...}, [props명, state명, ...])
        - 컴포넌트가 업데이트된 이후 실행되는 메소드
        - 2번째 파라미터 배열에 명시한 props나 state가 변경될 때만 실행
    3. componentWillUnmount → useEffect에서 리턴되는 일급함수 사용
        - 컴포넌트가 소멸(언마운트)될 때 호출
- 클라이언트/서버 사이드 렌더링
    - 클라이언트 사이드 렌더링
        - 서버 측에서 HTML, JS, Fetch API Data를 받아 사용자 측에서 렌더링을 하는 방식
        - 장점
            - 사용자의 행동에 따라 필요한 부분만 따로 읽어들이고 재렌더링을 하면 되기 때문에, 인터렉션 성능이 꽤 좋다
        - 단점
            - 페이지를 읽어들이고 JS 파일도 읽어들인 다음 화면까지 모두 그려야 사용자에게 보여지기 때문에 초기 구동 속도가 느린 편
            - 웹 크롤러가 JavaScript를 사용하지 못하기에 검색 엔진 최적화 문제도 존재
            - 사용자 정보를 쿠키 말고는 딱히 저장하기 힘들다는 보안 문제도 존재
    - 서버 사이드 렌더링
        - 서버 측에서 전체적인 HTML을 렌더링한 뒤 사용자에게 전송하는 방식
        - 장점
            - 초기 구동을 조금 더 앞당길 수 있다
        - 단점
            - 조금만 변경되어도 서버 측에서 전체 재렌더링을 해야 하기 때문에 인터렉션 성능은 아쉬운 편
- props와 state
    - props
        - 자식 컴포넌트가 부모 컴포넌트에게서 받는 데이터
        - 변경 불가능
    - state
        - 컴포넌트의 생명 주기 동안 수정될 수 있는 컴포넌트 내부 데이터
        - 변경 후 재렌더링 시에도 유지 가능
- setState
    - 컴포넌트의 state를 변경시키는 함수
    - 사용하는 이유?
        - this.state = ...; 등등으로 state를 직접 변경할 경우, React에서 이 변경 사항을 알아낼 방법이 없음
        - React에 어떤 상태가 변경되었다고 알려줌으로써 재렌더링을 실시하게 함