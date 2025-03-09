# redux-logger

#### 설치하기

```sh
$ yarn add redux-logger
```

#### 사용하기

```js
(...)
import { applyMiddleware, legacy_createStore as createStore } from 'redux';
import rootReducer from "./modules";
import { logger } from 'redux-logger';

const store = createStore(rootReducer, applyMiddleware(logger));
```
