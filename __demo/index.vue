<template>
<div class="parent" @click="btnClick()"><div class="child" @click="proxy($event)">子元素决定是否冒泡</div>父元素角落瑟瑟发抖~~</div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
  },
  methods: {
    btnClick() {
      alert('汉献帝: 我真的会谢~~');
    },
    proxy($event) {
      const confirm = window.confirm("确认冒泡?")
      !confirm && $event.stopPropagation()
    }
  }
}
</script>

<style lang="less">
.parent {
    width: 200px;
    height: 100px;
    pointer-events: none; /* 关闭元素鼠标事件 */
    position: relative;
     border: steelblue 5px solid;
     cursor: pointer;
     text-align: center;
}
.parent::after {
    content:'伪元素触发父元素的事件';
    position: absolute;
    right: -200px;
    top: 40px;
    pointer-events: auto; 
    border: red 3px solid;
  
}
.child {
    position: absolute;
    pointer-events: auto; 
    border: pink 3px solid;
    width: 100%;
    height: 100%;
    box-sizing: border-box;
     padding-top: 30px;
}
</style>
