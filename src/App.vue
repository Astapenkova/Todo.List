<template>
  <div class="todolist">
    <form @submit.prevent class="todo-header">
      <h1 class="title">Список задач</h1>
      <input
        :value="task"
        @input="valueTask"
        class="todo-inputtype"
        tape="text"
        placeholder="Укажите задачу"
      />
      <button @click="createTask" class="btn-oval">+</button>
    </form>

    <div class="todo-main">
      <ul class="todo-list">
        <li v-bind:key="t" v-for="(t, index) in listTask" class="todo-item">
          {{ t.task }}
          <button class="deleteTodo" @click="deleteTodo(index)">Удалить</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      listTask: [
        { id: 1, task: "Выполнить дизайн" },
        { id: 2, task: "Сделать верстку сайта" },
        { id: 3, task: "Загрузить сайт" },
      ],
      task: " ",
      data: 0,
    };
  },

  methods: {
    valueTask(event) {
      this.task = event.target.value;
    },
    createTask() {
      const newTask = {
        id: Date.now(),
        task: this.task,
      };
      console.log(newTask);
      this.listTask.push(newTask);
      this.task = "";
    },
    deleteTodo(index) {
      this.listTask.splice(index, 1);
    },
  },
};
</script>

<style scope>
.title {
  margin-top: 20px;
  font-size: 40px;
  text-align: center;
  margin-bottom: 30px;
  color: white;
  text-shadow: rgb(5, 0, 0) 10px 0 10px;
}
.todo-inputtype {
  padding: 10px 20px;
  border: 3px solid rgba(0, 0, 0, 0.375);
  border-radius: 10px;
  -webkit-box-shadow: 19px 19px 20px 7px rgba(27, 30, 32, 0.2);
  -moz-box-shadow: 19px 19px 20px 7px rgba(27, 30, 32, 0.2);
  box-shadow: 19px 19px 20px 7px rgba(27, 30, 32, 0.2);
  width: 300px;
}

.btn-oval {
  display: inline-block;
  margin: 20px;
  width: 40px;
  height: 40px;
  box-sizing: border-box;
  text-align: center;
  color: #fff;
  text-decoration: none;
  background: linear-gradient(#89c13e, #599c02);
  background-color: #6fad1d;
  border-radius: 35px;
  border: 1px solid #579a00;
  font: bold 30px/10px Arial;
  box-shadow: inset 0 2px 2px #cce464, inset 1px 0 3px #b2dc2d,
    inset -1px 0 3px #b2dc2d, inset 0 -2px 2px #89d301,
    0 0 3px rgba(0, 0, 0, 0.24);
  position: relative;
  text-shadow: 0 1px #45880d;
  outline: none;
}

.btn-oval:hover {
  background: linear-gradient(#97d444, #65ad07);
  box-shadow: inset 0 1px 0 #e2f498, inset 0 2px 0 #ceec87,
    inset 0 3px 0 #c3e67c, inset 0 5px 0 #bae475, inset 1px 0 3px #b2dc2d,
    inset -1px 0 3px #b2dc2d, inset 0 -2px 2px #89d301,
    0 0 3px rgba(0, 0, 0, 0.24);
}
.btn-oval:active {
  background: linear-gradient(#83bb37, #599c02);
  box-shadow: inset 0 3px 7px #3c7b00;
  padding: 1px 0 0 1px;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(#8d0d76, #f6f6f87a);
  background-repeat: no-repeat;
}
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 100px;
  margin-top: 75px;
}

.todo-main {
  margin-top: 20px;
}
.todo-list {
  list-style: none;
  margin: 0;
  padding: 0;
  font-size: 0;
}
.todo-item {
  display: flex;
  font-size: 20px;
  color: #000;
  padding: 5px 30px;
  background-color: #fff;
  margin-top: 5px;
  margin-bottom: 5px;
  border-radius: 15px;
  border: 3px solid rgba(0, 0, 0, 0.375);
  -webkit-box-shadow: 19px 19px 20px 7px rgba(27, 30, 32, 0.2);
  -moz-box-shadow: 19px 19px 20px 7px rgba(27, 30, 32, 0.2);
  box-shadow: 19px 19px 20px 7px rgba(27, 30, 32, 0.2);
}
.deleteTodo {
  margin-left: auto;
  background-color: rgba(255, 0, 0, 0.416);
  border-radius: 15px;
  border: 3px solid rgba(0, 0, 0, 0.375);
  -webkit-box-shadow: 19px 19px 20px 7px rgba(27, 30, 32, 0.2);
  -moz-box-shadow: 19px 19px 20px 7px rgba(27, 30, 32, 0.2);
  box-shadow: 19px 19px 20px 7px rgba(27, 30, 32, 0.2);
  width: 70px;
  height: 30px;
}
.deleteTodo:hover {
  color: rgba(255, 0, 0, 0.416);
}
.deleteTodo:active {
  background: linear-gradient(rgba(255, 0, 0, 0.416));
  box-shadow: inset 0 3px 7px rgba(123, 3, 3, 0.962);
  padding: 1px 0 0 1px;
}
</style>
