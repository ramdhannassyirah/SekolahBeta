<template>
  <div>
    <h1>Task Manager</h1>
    <form @submit.prevent="addTask">
      <label for="task">Tambahkan Tugas:</label>
      <input id="task" v-model="newTask" type="text" />
      <button type="submit">Tambah</button>
    </form>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">{{ task }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: '', // Input baru untuk tugas
      tasks: [], // Array untuk menyimpan tugas
    }
  },
  methods: {
    addTask() {
      if (this.newTask.trim() === '') return // Jangan tambahkan tugas kosong

      this.tasks.push(this.newTask) // Menambahkan tugas baru ke dalam array
      this.newTask = '' // Mengosongkan input setelah menambahkan tugas
    },
  },
}
</script>
