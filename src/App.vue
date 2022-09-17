<template>
  <section class="todoapp">
    <!-- 除了驼峰, 还可以使用-转换链接 -->
    <TodoHeader @add-event="addtodolist"></TodoHeader>
    <TodoMain :list="list" @del-event="deltodolist"></TodoMain>
    <TodoFooter></TodoFooter>
  </section>
</template>

<script>
// 1.0 样式引入
import "./styles/base.css"
import "./styles/index.css"

import TodoHeader from "./components/TodoHeader";
import TodoMain from "./components/TodoMain";
import TodoFooter from "./components/TodoFooter";


export default {
  name: 'Todo',
  data () {
    return {
      list: [
        { id: 100, name: "吃饭", isDone: true },
        { id: 201, name: "睡觉", isDone: false },
        { id: 103, name: "打豆豆", isDone: true },
      ],
    }
  },
  methods: {
    //删除事件
    deltodolist (Id) {
      const index = this.list.findIndex(item => item.id === Id)
      this.list.splice(index, 1)
    },
    //添加事件
    addtodolist (taskname) {
      let id = this.list.length === 0 ? 100 : this.list[this.list.length - 1].id + 1
      this.list.push({
        id: id,
        name: taskname,
        isDone: false
      })
    }
  },
  components: {
    TodoHeader,
    TodoMain,
    TodoFooter,
  },
};
</script>