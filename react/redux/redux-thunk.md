# redux-thunk

`redux-thunk`는 비동기 작업을 처리할 때 가장 많이 사용하는 `미들웨어`이다. 객체가 아닌 함수 형태의 액션을 디스패치할 수 있게 해준다.

```sh
$ yarn add redux-thunk
```

스토어를 만들 때 redux-thunk를 적용한다.

```js
(...)
import { createStore, applyMiddleware } from 'redux';
import { thunk } from 'redux-thunk';
import rootReducer from './reducers';

const store = createStore(rootReducer, applyMiddleware(thunk));

(...)
```
