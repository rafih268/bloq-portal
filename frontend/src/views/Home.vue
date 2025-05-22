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
    <div class="absolute inset-y-0 start-0 flex items-center ps-3 pointer-events-none">
      <svg class="w-4 h-4 text-gray-500 dark:text-gray-400" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 20 20">
        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z"/>
      </svg>
      <span class="sr-only">Search icon</span>
    </div>
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