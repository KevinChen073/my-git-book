<!--
 * @Author: 星啸(陈远宏)
 * @Date: 2020-12-15 14:32:55
 * @LastEditTime: 2020-12-24 12:43:24
 * @LastEditors: 星啸(陈远宏)
 * @Description: 
 * @FilePath: /my-git-book/frontEnd/react.md
-->
react的一些新特性

## react16
- react hook：更强大的Life style hook。用于解决pure component和class component之间的一些问题。state、custom hook、effect hook
https://zhuanlan.zhihu.com/p/47684983
- array 返回：减少层级
- context正式列入使用：虽然违反redux，但是父级传入给子级属性很方便

- 在一个函数组件中使用多个 useState

### Hook的好处了解
对应到生命周期是可以的。而且在我理解初期，对应到生命周期确实帮助我更快了解了。
自定义hook则是可以用纯function的方式来达到类似声明周期的效果。
例如useState就是以前的setState的变种。useEffect则是以前渲染后变更的集合，例如didMount、didUpdate、willUnMount。我可以用更简洁的方式来书写我的逻辑了，直接导致了：代码可读性更高、可移植。最直观的一点是，UI和逻辑分离的成本变低。

例如我以前写一个Follow按钮，我可能需要在按钮内部控制状态，例如在didMount的时候进行事件绑定、UnMount的时候进行解绑，点击的时候发送通知。现在我可以写成
```javascript
function useFollow() {
    const [isFollow, setFollow] = useState(0);
    useEffect(()=>{
        Follow.getLink((rst)=>{
            setFollow(rst);
        });
        return ()=>{
            Follow.setClose();
        }
    }, []);
    return [isFollow, setFollow];
}

function FollowBtn() {
    const [isFollow, setFollow] = useFollow(0);
    return (
        <button
            onClick={setFollow}
        >
            {isFollow? '666' : 'follow'}
        </button>)
}
```

类似redux解决了state过多难以处理的问题，reducer做这个事情的，hook也是可以做的

### hook的实现
数组实现
useState可以理解为就是一个React维护的组件级别的Array和闭包。
1. 每次setState，就是触发了对应的闭包，更新state的值
2. 同时触发该组件的Render
3. 组件内的State（数组内的State）按照数组顺序重新计算