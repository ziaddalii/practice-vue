<!-- old way // vue 2 -->
<!-- <script>
export default {
  data() {
    return {
      name: 'Ziad Ali',
      status: 'active',
      tasks: ['task one', 'task two', 'task three'],
      link: 'https://google.com',
    }
  },
  methods: {
    toggleStatus() {
      if (this.status === 'active') {
        this.status = 'pending'
      } else if (this.status === 'pending') {
        this.status = 'inactive'
      } else {
        this.status = 'active'
      }
    },
  },
}
</script> -->

<script setup>
import { ref } from 'vue'

const name = ref('Ziad Ali')
const status = ref('active')
const tasks = ref(['task one', 'task two', 'task three'])
const link = ref('https://google.com')
const newTask = ref('')
const toggleStatus = () => {
  if (status.value === 'active') {
    status.value = 'pending'
  } else if (status.value === 'pending') {
    status.value = 'inactive'
  } else {
    status.value = 'active'
  }
}
const addTask = () => {
  if (newTask.value.trim() !== '') {
    tasks.value.push(newTask.value)
    newTask.value = ''
  }
}
const deleteTask = (index) => {
  tasks.value.splice(index, 1)
}
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">this user is active</p>
  <p v-else-if="status === 'pending'">this user is pending</p>
  <p v-else>this user is not-active</p>
  <form v-on:submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>
  <ul v-for="(task, i) in tasks" :key="task">
    <li>
      <span>{{ task }}</span>
      <button @click="deleteTask(i)">x</button>
    </li>
  </ul>
  <a :href="link">Go To Google</a>
  <button @click="toggleStatus">Change Status</button>
</template>

<style scoped></style>
