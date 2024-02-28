<template class="main">
  <div id="app">
    <h1>Список задач</h1>
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Добавить задачу" />
    <ul>
      <transition-group name="slide-fade">
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
        <button @click="removeTask(index)">Удалить</button>
      </li>
    </transition-group>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: []
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== '') {
        this.tasks.push(this.newTask);
        this.newTask = '';
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    }
  }
};

</script>

<style>
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active до версии 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}


body{
  background-color: #242424;
}

button {
  border-radius: 8px;
  border: 1px solid transparent;
  padding: 0.6em 1.2em;
  font-size: 1em;
  font-weight: 50;
  font-family: inherit;
  background-color: #1a1a1a;
  cursor: pointer;
  transition: border-color 0.25s;
}
button:hover {
  border-color: #ee59f3;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #ee6adc;
 
}

input {
  margin-bottom: 10px;
  padding: 20px;
  height: 25px;
  border-radius: 10px;
  background-color: #1a1a1a;
  font-size: 20px;
  transition: border-color 0.25s;
  text-decoration: #ee59f3;
}

input:hover {
  border-color: #ee59f3;
}
ul {
  list-style-type: none;
  padding: 10px;
}

li {
  margin-bottom: 10px;
  font-size: 20px;
}

button {
  margin-left: 10px;
  cursor: pointer;
}
</style>