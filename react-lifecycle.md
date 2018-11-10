# 浅谈 React Component Lifecycle（v16.3）
在React组件生命周期中总结起来就是四个过程，分别为：
Mounting、Updating、Unmounting、Error Handling，其中在整个生命周期中Mounting、Unmounting只会执行一次，更新则根据实际情况会执行多次，其中Error Handling过程是在组件发生异常时执行。
接下来就以此介绍一个这四个过程。
## Mounting 挂载
当创建的组件实例插入到DOM树时，以下生命周期函数将按此顺序调用执行：
1. `constructor(props, state, updator)`
2. `static getDerivedStateFromProps()`
3. `render()`
4. `componentDidMount()`

## Updating 更新
当组件props或state更新时，组件将被重新渲染（re-render）并且以下的生命周期函数将按照此顺序调用执行：
1. `static getDerivedStateFromProps()`
2. `shouldComponentUpdate()`
3. `render()`
4. `getSnapshotBeforeUpdate()`
5. `componentDidUpdate`

## Unmounting 卸载
组件从Dom树中被移除时被调用：
`componentWillUnMounting()`

## Error Handling 错误处理
组件渲染时发生异常时，以下的生命周期函数将按照此顺序调用执行：
1. `static getDerivedStateFromError()`
2. `componentDidCatch()`

![React Component Lifecycle](media/React%20Component%20Lifecycle.png)
