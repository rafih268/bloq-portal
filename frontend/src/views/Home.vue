<script setup>
import { ref, computed } from 'vue';
import StudentCard from '@/components/StudentCard.vue';

const students = ref([
  { id: 1, name: 'Bonnie Green', year: 11 },
  { id: 2, name: 'Tom White', year: 10 },
  { id: 3, name: 'Alice Black', year: 9},
]);

const searchQuery = ref('');

const filteredStudents = computed(() => {
  const query = searchQuery.value.toLowerCase();
  return students.value.filter(student => student.name.toLowerCase().includes(query));
});
</script>

<template>
  <div class="min-h-screen flex flex-col items-center justify-start p-6 bg-amber-50">
    <!-- Search Bar -->
    <input
      v-model="searchQuery"
      type="text"
      placeholder="Search students..."
      class="w-full max-w-md p-2 mb-4 bg-white shadow-sm border border-transparent rounded-md focus:border-amber-300 focus:ring-amber-200 focus:outline-none transition duration-200"
    />

    <!-- List of Student Cards -->
    <div class="flex flex-col items-center gap-6">
      <StudentCard
        v-for="student in filteredStudents"
        :key="student.id"
        :name="student.name"
        :year="student.year"
      />
    </div>
  </div>
</template>