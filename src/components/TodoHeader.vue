<template>
  <header class="header">
    <h1>todos</h1>
    <input id="toggle-all" class="toggle-all" type="checkbox" />
    <label for="toggle-all"></label>
    <input
      v-model="task"
      class="new-todo"
      placeholder="输入任务名称-回车确认"
      autofocus
      @keydown.enter="add(task)"
    />
  </header>
</template>

<script>
export default {
  data () {
    return {
      task: ''
    }
  },
  methods: {
    add () {
      this.$emit("add-event", this.task)
      this.task = ''
    }
  }
}
</script>