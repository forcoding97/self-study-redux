# Redux

> 우선 지금은 Redux 에 대해 완벽하게 이해하기 보다는, <br/>
> Redux 에서 사용되는 용어들에 익숙해진다는 느낌으로 학습하도록 하자.

<br/>

## Redux Element

- state <br/>
  : 상태로 저장된 값
- getState <br/>
  : 현재 state 값을 불러오는 함수

  ```javascript
  function reducer(state, action) {
    if (state === undefined) {
      return { color: 'yellow' };
    }
  }
  var store = Redux.createStore(reducer);
  console.log(store.getState()); // { color: 'yellow' }
  ```

- render <br/>
  : state 값에 따라 다르게 렌더링되게 해주는 함수
- reducer <br/>
  : state 의 값을 변경하는 함수 기존의 state 값과 action 을 통해 새로운 state 값을 return 해주면, <br/>
  &nbsp; return 된 값이 새로운 state 가 된다.

  ```javascript
  function reducer(state, action) {
    if (state === undefined) {
      return { color: 'yellow' };
    }
    var newState;
    if (action.type === 'CHANGE_COLOR') {
      newState = Object.assign({}, state, { color: action.color });
    }
    return newState;
  }
  var store = Redux.createStore(reducer);

  // store.dispatch({ type: 'CHANGE_COLOR', color: 'red' }); 을 실행
  console.log(store.getState()); // { color: 'red' }
  ```

- dispatch <br/>
  : state 값을 변경하는 함수
- subscribe <br/>
  : dispatch 를 통해 값이 변경되었을 때 구동될 함수들을 등록해주는 함수

#### ? 그럼 reducer 와 dispatch 의 차이는 무엇일까

- 아직 정확하진 않지만, reducer 는 state 를 변경시키는 기계 그 자체에 비유한다면 <br/>
  dispatch 는 state 를 변경시키는 기계 즉, reducer 에 사용되는 action 이라는 나사를 포함한 톱니바퀴에 비유할 수 있을 것 같다.

<br/>

## Why should we use Redux ?

- 중앙집중적인 데이터 스토어를 통해서 어플리케이션을 쉽게 개발할 수 있다.
