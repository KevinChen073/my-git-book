# redux-saga
使用generator以及promise方案控制redux的异步流程同步化

## generator&Promise
generator和Promise如何把异步流程同步化。
假定有函数Q.async();他会对传入的生成器函数实例化，并且在这个函数的Promise.resolve()被调用时去调用生成器的next()，这样，就可以变成：
``` javascript
var all = Q.async(function* () {
    var src = yield getData(); // 一个异步promise
    var img = yield getImg(src); // 又一个异步promise
    showImg(img);
});

all();
```

## redux中有可能异步的地方
- 调用异步方法 `sage.call`
- 异步方法后分发action `sage.put`
- 等待其他分发action `sage.take`
- 触发其他生成器 `sage.fork`

## 实际用法
redux可以允许我们拦截action，并且做一些中间处理，这时候，这些中间处理如何同步编写，就需要用到saga了。
如下的流程为：
其他组件dispatch('FETCH_TODOS') ->
被中间件拦截，开始调用watchTodos的中间件，这时候对watchTodos的生成器wt.next() ->
watchTodos执行到take('FETCH_TODOS') -> 
take受到反馈，生成器再次被next,wt.next() ->
调用fork(loadTodos) ->
开始put(FETCHING_TODOS)，call(fetch) -> 
call完结后，再次调用wt.next() -> 
下一个put(FETCHED_TODOS) ->
把相关的payload数据传到store，并且结束这次中间件。等待下一次的watch
> ps:应该不需要用while这么暴力的行为的
``` javascript
import { fork, take } from 'redux-saga';

function* loadTodos() {
  yield put({ type: 'FETCHING_TODOS' });
  const todos = yield call(fetch, '/todos');
  yield put({ type: 'FETCHED_TODOS', payload: todos });
}

function* watchTodos() {
  while(yield take('FETCH_TODOS')) {
    yield fork(loadTodos);
  }
}

// 我们需要更新saga常量
createStoreWithSaga = applyMiddleware(
  sagaMiddleware([watchTodos])
)(createStore);
```
> 作者：uncle_charlie
> 链接：https://www.jianshu.com/p/ec2d93cf70b3
> 來源：简书
> 简书著作权归作者所有，任何形式的转载都请联系作者获得授权并注明出处。
