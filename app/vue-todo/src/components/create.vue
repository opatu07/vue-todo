<script setup>
import { ref } from "vue";

const newTask = ref("");  // 入力されたタスク
const tasks = ref([]);    // タスクのリスト

// タスクを追加する関数
const addTask = (event) => {
  event.preventDefault();  // フォーム送信のリロードを防ぐ
  if (newTask.value.trim() === "") return;

  tasks.value.push({ text: newTask.value, completed: false });
  newTask.value = "";  // 入力欄をクリア
};
</script>

<template>
  <div>
    <!-- フォームを使う -->
    <form @submit="addTask">
      <input v-model="newTask" placeholder="新しいタスクを入力" />
    </form>

    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task.text }}
      </li>
    </ul>
  </div>
</template>
<style scoped>

</style>

