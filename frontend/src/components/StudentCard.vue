<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';

defineProps({
  name: String,
  year: [String, Number],
});

const isDropdownOpen = ref(false);

const toggleDropdown = () => {
  isDropdownOpen.value = !isDropdownOpen.value;
};

const dropdownRef = ref(null);

const handleClickOutside = (event) => {
  if (dropdownRef.value && !dropdownRef.value.contains(event.target)) {
    isDropdownOpen.value = false;
  }
};

onMounted(() => {
  document.addEventListener("click", handleClickOutside);
})

onBeforeUnmount(() => {
  document.removeEventListener("click", handleClickOutside);
})
</script>

<template>
  <div class="w-full max-w-md bg-amber-100 border border-amber-200 rounded-lg shadow-sm">
    <!-- Header -->
    <div class="flex justify-between items-center px-3 pt-3">
      <img
        class="w-10 h-10 rounded-full shadow-lg"
        src="../assets/img/Profile User free icons designed by Freepik.jpeg"
        alt="Student Image"
      />

      <div class="relative" ref="dropdownRef">
        <button
          @click="toggleDropdown"
          class="inline-block text-gray-400 hover:bg-gray-700 rounded-lg text-sm p-1.5"
          type="button"
        >
          <span class="sr-only">Open dropdown</span>
          <svg
            class="w-5 h-5"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            fill="currentColor"
            viewBox="0 0 16 3"
          >
            <path d="M2 0a1.5 1.5 0 1 1 0 3 1.5 1.5 0 0 1 0-3Zm6.041 0a1.5 1.5 0 1 1 0 3 1.5 1.5 0 0 1 0-3ZM14 0a1.5 1.5 0 1 1 0 3 1.5 1.5 0 0 1 0-3Z"/>
          </svg>
        </button>
  
        <!-- Dropdown menu -->
        <div
          v-if="isDropdownOpen"
          class="z-10 absolute right-0 mt-2 text-base list-none bg-gray-700 divide-y divide-gray-100 rounded-lg shadow-sm w-44">
          <ul class="py-2" aria-labelledby="dropdownButton">
            <li>
              <a href="#" class="block px-4 py-2 text-sm text-gray-200 hover:text-white hover:bg-gray-600">
                Edit
              </a>
            </li>
            <li>
              <a href="#" class="block px-4 py-2 text-sm text-gray-200 hover:bg-gray-600 hover:text-white">
                Archive
              </a>
            </li>
            <li>
              <a href="#" class="block px-4 py-2 text-sm text-gray-200 hover:bg-gray-600 hover:text-white">
                Delete
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>

    <!-- Info -->
    <div class="p-3">
      <div class="flex items-center justify-between gap-x-8">
        <div>
          <p class="text-md font-medium text-gray-900">{{ name }}</p>
          <p class="text-sm text-gray-600">Year: {{ year }}</p>
        </div>
        <div class="flex gap-2">
          <button type="button" class="text-white bg-gray-800 hover:bg-gray-900 font-medium rounded-full text-sm px-4 py-1.5">
            View Profile
          </button>
          <button type="button" class="text-black hover:text-white border border-gray-900  hover:bg-gray-700 font-medium rounded-lg text-sm px-4 py-1.5 text-center transition duration-200 ease-in-out">
            Send Message
          </button>
        </div>
      </div>
    </div>
  </div>
</template>