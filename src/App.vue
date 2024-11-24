<script>
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
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">this user is active</p>
  <p v-else-if="status === 'pending'">this user is pending</p>
  <p v-else>this user is not-active</p>
  <div v-for="task in tasks" :key="task">{{ task }}</div>
  <a :href="link">Go To Google</a>
  <button @click="toggleStatus">Change Status</button>
</template>

<style scoped></style>
