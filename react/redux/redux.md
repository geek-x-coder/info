# Redux

## 개요

- 리덕스는 가장 많이 사용되는 리액트 상태 관리 라이브러리
- 컴포넌트의 상태 업데이트 관련 로직을 다른 파일로 분리시켜서 효율적으로 관리 가능
- 컴포넌트끼리 똑같은 상태를 공유 할 시에도 여러 컴포넌트를 거치지 않고 손쉽게 상태 값 전달 및 업데이트 가능
- 코드의 유지 보수성 증대 / 작업 효율 극대화 / 강력한 개발자 도구 지원 / 비동기 작업을 효율적으로 할 수 있는 미들웨어 기능 제공

### 액션(action)

- 상태에 어떠한 변화가 필요하면 액션(action)이란 것이 발생
- 액션 객체는 type 필드를 반드시 가지고 있어야 함

```js
// 예시1
{
	type : 'ADD_TODO',
	data : {
		id: 1,
		text: '리덕스 배우기'
	}
}

// 예시2
{
	type : 'CHANGE_INPUT',
	text: '안녕하세요'
}
```

### 액션 생성 함수

- 액션 생성 함수(action creator)는 액션 객체를 만들어 주는 함수

```js
function addTodo(data) {
  return {
    type: "ADD_TODO",
    data,
  };
}
```

### 리듀서

- 리듀서(reducer)는 변화를 일으키는 함수
- 액션을 만들어서 발생시키면 리듀서가 현재 상태와 전달받은 액션 객체를 파라미터로 받아 옴
- 두 값을 참고하여 새로운 상태를 만들어서 반환

```js
const initialState = {
  counter: 1,
};

function reducer(state = initialState, action) {
  switch (action.type) {
    case "INCREMENT":
      return {
        counter: state.counter + 1,
      };
    default:
      return state;
  }
}
```

### 스토어 (store)

- 프로젝트에 리덕스를 적용하기 위해서는 스토어(store)를 만들어야 함
- 한 개의 프로젝트는 단 하나의 스토어만 가질 수 있음
- 스토어 안에는 현재 애플리케이션 상태와 리듀서가 들어가 있으며, 그 외에도 몇 가지 중요한 내장 함수가 있음

### 디스패치

- 디스패치(dispatch)는 스토어의 내장 함수 중 하나
- 디스패치는 '액션을 발생시키는 것'
- dispatch(action)과 같은 형태로 액션 객체를 파라미터로 넣어서 호춮
- 이 함수가 호출되면 스토어는 리듀서 함수를 실행시켜서 새로운 상태를 반환\

### 구독

- 구독(subscribe)도 스토어의 내장 함수 중 하나
- subscribe 함수 안에 리스너 함수를 파라미터로 넣어서 호출해 주면, 리스너 함수가 액션이 디스패치되어 상태가 업데이트 될 때마다 호출됨
