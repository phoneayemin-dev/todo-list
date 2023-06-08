<template>
  <section>
    <div class="container">
      <div class="title">{{ title }}</div>
      <div>
        <input type="text" v-model="newTask" @keyup.enter="add()">
        <button type="submit" :disabled="newTask.length < 1" @click="add">ADD</button>
      </div>
      <ul class="tasks">
        <li v-for="(task, index) in tasks" :key="index">
          <div>
            <span>{{ task }}</span>
            <button type="submit" @click="deleteTask(index)">DELETE</button>
          </div>
        </li>
      </ul>
      <div>
        <button type="submit" @click="deleteAll()">DELETE ALL</button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data(){
    return {
      title: "To Do List",
      newTask: "",
      tasks: [
        "Task One",
        "Task Two"
      ]
    }    
  },
  methods: {
    add(){
      const vm = this
      vm.tasks.push(vm.newTask)
    },
    deleteAll(){
      const vm = this
      vm.tasks = []
    },
    deleteTask(index){
      const vm = this
      console.log(index)
      if (vm.tasks.length > 0) {
        vm.tasks = vm.tasks.filter( (task, idx) => idx != index)
      }
    }
  },
}
</script>

<style lang="css" scoped>
  @import url("../assets/css/style.css");
</style>
