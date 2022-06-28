<template>
<div class="container" id="elzero-app">
    <form>
      <input type="text" placeholder="Type Your Task" v-model="taskText"/>
      <button @click.prevent="addTask" :disabled="!taskText">Add Task</button>
      <button class="delete-all" v-if="tasks.length &gt; 1" @click.prevent="deleteAll">Delete All</button>
    </form>
    <div class="tasks-list" v-for="(task, index) in tasks">
        <div class="task-box" @click="task.done = !task.done" :style="{ 'text-decoration': task.done ? 'line-through' : '' }">{{ task.words }}</div>
        <div class="delete" @click="deleteTask(index)">Delete</div>
    </div>
</div>
</template>

<script>
export default {
  name:"Table",
  data(){
    return{
    tasks: [],
    taskText: ""  
    }
  },
  methods: {
    addTask: function() {
      this.tasks.push({ words: this.taskText, done: false });
      this.taskText = "";
      console.log(this.tasks)
    },
    deleteTask: function(index) {
      this.tasks.splice(index, 1);
    },
    deleteAll: function() {
      this.tasks = [];
    }
  }
}
</script>

<style lang='scss' scoped>
* {
  box-sizing: border-box;
}
.container {
  text-align: center;
  form {
    margin: 20px auto 10px;
    width: 500px;
    overflow: hidden;
    input {
      background-color: #f7f7f7;
      border: 1px solid #eee;
      margin-bottom: 15px;
      width: calc(100% - 210px);
      height: 46px;
      padding: 10px;
      float: left;
      &:focus {
        outline: none;
      }
    }
    button {
      width: 90px;
      height: 46px;
      padding: 10px;
      background-color: #2196f3;
      color: #fff;
      border-color: transparent;
      cursor: pointer;
      float: left;
      margin-left: 5px;
      &:disabled {
        opacity: 0.4;
        cursor: no-drop;
      }
      &:focus {
        outline: none;
      }
      &.delete-all {
        width: 110px;
        background-color: #f44336;
      }
    }
  }
  .tasks-list {
    width: 500px;
    margin: 0 auto;
    .task-box {
      background-color: rgba(139, 195, 74, 0.25);
      padding: 15px;
      text-align: left;
      margin-bottom: 15px;
      margin-right: 5px;
      width: calc(100% - 86px);
      cursor: pointer;
      float: left;
    }
    .delete {
      float: right;
      width: 80px;
      background-color: #f44336;
      color: #fff;
      border-color: transparent;
      padding: 1px 10px;
      cursor: pointer;
      height: 48px;
      line-height: 51px;
    }
  }
}
.links-urls {
  position: absolute;
  bottom: 0;
  right: 0;
  padding: 10px;
  .link {
    padding: 10px 20px;
    display: block;
    background-color: #EEE;
    margin-bottom: 10px;
    text-decoration: none;
    color: #777;
  }
}
</style>