<template>
  <div>
    <select v-model="selectedCategory">
      <option value="">Semua Kategori</option>
      <option v-for="category in categories" :key="category">
        {{ category }}
      </option>
    </select>

    <ul>
      <li v-for="task in filteredTasks" :key="task.id">
        {{ task.name }} - {{ task.category }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        { id: 1, name: 'Tugas 1', category: 'Pekerjaan' },
        { id: 2, name: 'Tugas 2', category: 'Belajar' },
        { id: 3, name: 'Tugas 3', category: 'Pekerjaan' },
        // Tambahkan data tugas dengan properti category
      ],
      selectedCategory: '',
    }
  },
  computed: {
    categories() {
      // Ambil daftar kategori unik dari tasks
      const uniqueCategories = [
        ...new Set(this.tasks.map((task) => task.category)),
      ]
      return uniqueCategories
    },
    filteredTasks() {
      // Filter tugas berdasarkan kategori yang dipilih
      if (this.selectedCategory === '') {
        return this.tasks // Tampilkan semua tugas jika tidak ada kategori yang dipilih
      } else {
        return this.tasks.filter(
          (task) => task.category === this.selectedCategory
        )
      }
    },
  },
}
</script>
