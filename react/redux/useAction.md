# useActions

유틸 Hook을 만들어서 사용
 > src/lib/useActions.js

```js 
import { bindActionCreators } from 'redux';
import { useDispatch } from 'react-redux';
import { useMemo } from 'react';

export default function useActions(actions, deps) {
	const dispatch = useDispatch();
	return useMemo(
		() => {
			if (Array.isArray(actions)) {
				return actions.map(a => bindActionCreators(a, dispatch));
			}
		return bindActionCreators(actions, dispatch);
		},
		deps ? [dispatch, ...deps] : deps
	);
}
```

`useActions` Hook은 액션 생성 함수를 액션을 디스패치하는 함수로 변환해줍니다. 액션 생성 함수를 사용하여 액션 객체를 만들고, 이를 스토어에 디스패치하는 작업을 해 주는 함수를 자동으로 만들어 준다.

useActions는 두 가지 파라미터가 필요하다. 첫 번째 파라미터는 액션 생성 함수로 이루어진 배열이다.
두 번째 파라미터는 deps 배열이며, 이 배열 안에 들어 있는 원소가 바뀌면 액션을 디스패치하는 함수를 새로 만들게 된다.