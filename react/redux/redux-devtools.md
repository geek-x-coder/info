# redux devtools

#### 설치하기

```sh
yarn add @redux-devtools/extension
```

#### 사용하기

```js
import { composeWithDevTools } from "@redux-devtools/extension";

const store = createStore(rootReducer, composeWithDevTools());

// 또는 아래와 같이 사용하기도 한다. (import 없앨 수 있음)

const store = createStore(
   reducer, /* preloadedState, */
window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
 );
```

이후에 크롬 웹스토어에서 `redux devTools`를 다운받아서 설치/사용  
