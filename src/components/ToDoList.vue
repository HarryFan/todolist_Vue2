<template>
  <div id="customer-support-todo-list">
    <h2>客戶支援待辦事項</h2>
    <input type="text" v-model="newTask" @keyup.enter="addTask" placeholder="新增待辦事項">
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
        <button @click="removeTask(index)">刪除</button>
      </li>
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
      if (this.newTask.trim()) {
        this.tasks.push(this.newTask.trim());
        this.newTask = '';
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    }
  }
};
</script>

<style scoped>
#customer-support-todo-list {
  max-width: 500px;
  margin: 0 auto;
}

input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
}

ul {
  padding: 0;
}

li {
  list-style-type: none;
  background-color: #f3f3f3;
  padding: 10px;
  margin-bottom: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

button {
  background-color: red;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}
</style>
