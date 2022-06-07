
<template>
  <div>
    <div class="container">
      
      <div class="forms">
        <input v-model="taskText" placeholder="Your task...">
        <div class="forms__button">
          <button v-on:click="addTask">Add Task</button>
        </div>
      </div>
      
      <div class="tasks-body">
        <div class="tasks-body__title">Tasks</div>
        <div v-if="isTasksEmpty" class="tasks-body__emoji">
          ~( ˘▾˘~)
          <br>
          <span>just chill bro... u no need to work</span>
        </div>
        <ul v-else v-for="task in tasks" class="tasks">
          <li class="tasks__item">{{ task }}</li>
        </ul>
      </div>
      
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [],
      taskText: '',
      isTasksEmpty: true,
    }
  },
  methods: {  
    addTask() {
      if (!this.taskText) {
        return
      }

      this.tasks.push(this.taskText)
      this.isTasksEmpty = false
      this.taskText = ''
    },    
  }
}
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
}

ul { list-style-type: none; }
 
.container {
  max-width: 850px;
  margin: 0 auto;
  padding: 85px 20px 20px 20px;
}
.forms {
  display: flex;
  flex-direction: column;
  padding-bottom: 20px;
}
.forms input {
  font-size: 30px;
  height: 50px;
  margin-bottom: 15px;
  padding: 5px 15px;
}
.forms__button {
  align-self: flex-end;
}
.forms__button button{
  font-size: 20px;
  padding: 5px 30px;
}

.tasks-body__title {
  font-size: 40px;
  font-weight: bold;
  margin-bottom: 13px;
}

.tasks:not(:last-child) {
  margin-bottom: 10px;
}

.tasks__item {
  padding: 15px;
  border: 3px solid rgb(47, 135, 164);
  font-size: 25px;
  border-radius: 5px;
}

.tasks-body__emoji {
  font-size: 50px;
  margin-top: 30px;
  font-style: italic;
  text-align: center;
  opacity: 0.5;
  user-select: none;
}

.tasks-body__emoji span{
  font-size: 25px;
}

</style>