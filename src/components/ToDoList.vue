<template>
  <div id="customer-support-todo-list">
    <h2>客戶支援待辦事項</h2>
    <!-- 使用 v-model 綁定 newTask 變數，當使用者按下 Enter 鍵時觸發 addTask 方法 -->
    <input type="text" v-model="newTask" @keyup.enter="addTask" placeholder="新增待辦事項">
    <ul>
      <!-- 使用 v-for 顯示 tasks 陣列中的每一個項目 -->
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
        <!-- 當使用者點擊刪除按鈕時觸發 removeTask 方法 -->
        <el-button type="danger" icon="el-icon-delete" circle @click="removeTask(index)"></el-button>
      </li>
    </ul>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        newTask: '',
        tasks: [] // 建立 tasks 陣列
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim()) { // 檢查 newTask 是否為空字串
          this.tasks.push(this.newTask.trim()); // 將 newTask 加入 tasks 陣列中
          this.newTask = ''; // 清空 newTask 變數
        }
      },
      removeTask(index) {
        this.tasks.splice(index, 1); // 從 tasks 陣列中刪除指定索引的項目
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