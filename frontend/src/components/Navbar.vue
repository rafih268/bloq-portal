<script setup>
</script>

<template>
  <nav class="border-amber-200 bg-amber-300">
    <div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-1">
      <a href="https://techbloq.co.uk/" class="flex items-center space-x-3">
        <img src="../assets/img/techbloq-logo-site-1.png" class="h-16" alt="Techbloq Logo" />
      </a>
      <button data-collapse-toggle="navbar-solid-bg" type="button" class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200" aria-controls="navbar-solid-bg" aria-expanded="false">
        <span class="sr-only">Open main menu</span>
        <svg class="w-5 h-5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 17 14">
          <path
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M1 1h15M1 7h15M1 13h15"
          />
        </svg>
      </button>
      <div class="hidden w-full md:block md:w-auto" id="navbar-solid-bg">
        <ul class="flex flex-col font-medium mt-4 rounded-lg bg-gray-50 md:space-x-8 md:flex-row md:mt-0 md:border-0 md:bg-transparent">
          <li>
            <router-link
              to="/"
              class="block py-2.5 px-4 text-black rounded-sm hover:bg-black border-0 hover:text-white transition duration-200 ease-in-out"
            >
              Home
            </router-link>
          </li>
          <li>
            <router-link to="/about" class="block py-2.5 px-4 text-black rounded-sm hover:bg-black border-0 hover:text-white transition duration-75 ease-in-out">
              About
            </router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>