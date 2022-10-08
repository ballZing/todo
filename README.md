# 全局事件总线

## 1.一种组件间通信的方式，适用于<span style="color: red;">任意组件间通信<span>

## 2.安装全局事件总线
```javascript
new Vue({
    ...........................
    beforeCreate() {
        Vue.prototype.$bus = this
    },
    ...........................
})
```

## 3.使用事件总线
1. 接收数据：A组件想接收数据，则在A组件中给$bus绑定自定义事件，事件的<span style="color: red;">回调留在A组件自身</span>
```JavaScript
methods: {
    demo(data){....}
}
mounted() {
    this.$bus.$on('xxxx', this.demo)
}
```


2. 提供数据：`this.$bus.$emit('xxxx', 数据)`

## 4.最好在beforeDestroy钩子中，使用$off去解绑当前组件所用到的事件