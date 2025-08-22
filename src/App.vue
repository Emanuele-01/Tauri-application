<script setup lang="ts">
import { ref } from "vue";
import { invoke } from "@tauri-apps/api/core";


const greetMsg = ref("");
const name = ref("");

async function greet() {
  // Learn more about Tauri commands at https://tauri.app/develop/calling-rust/
  greetMsg.value = await invoke("greet", { name: name.value });
}
</script>

<template>
  <main class="m-0 pt-[10vh] flex flex-col justify-center text-center min-h-screen bg-gray-100 text-gray-900 font-sans antialiased dark:bg-gray-800 dark:text-gray-100">
    <h1 class="text-center text-red-500">Welcome to Tauri + Vue</h1>

    <div class="flex justify-center">
      <a href="https://vite.dev" target="_blank" class="font-medium text-blue-600 no-underline hover:text-blue-500 dark:hover:text-cyan-400">
        <img src="/vite.svg" class="h-24 p-6 transition-all duration-700 will-change-[filter] hover:drop-shadow-[0_0_2em_#747bff]" alt="Vite logo" />
      </a>
      <a href="https://tauri.app" target="_blank" class="font-medium text-blue-600 no-underline hover:text-blue-500 dark:hover:text-cyan-400">
        <img src="/tauri.svg" class="h-24 p-6 transition-all duration-700 will-change-[filter] hover:drop-shadow-[0_0_2em_#24c8db]" alt="Tauri logo" />
      </a>
      <a href="https://vuejs.org/" target="_blank" class="font-medium text-blue-600 no-underline hover:text-blue-500 dark:hover:text-cyan-400">
        <img src="./assets/vue.svg" class="h-24 p-6 transition-all duration-700 will-change-[filter] hover:drop-shadow-[0_0_2em_#249b73]" alt="Vue logo" />
      </a>
    </div>
    <p class="mb-4">Click on the Tauri, Vite, and Vue logos to learn more.</p>

    <form class="flex justify-center gap-2" @submit.prevent="greet">
      <input 
        id="greet-input" 
        v-model="name" 
        placeholder="Enter a name..." 
        class="rounded-lg border border-transparent px-5 py-2 text-base font-medium bg-white text-gray-900 transition-colors duration-250 shadow-md outline-none hover:border-blue-500 dark:bg-gray-900/60 dark:text-white"
      />
      <button 
        type="submit"
        class="rounded-lg border border-transparent px-5 py-2 text-base font-medium bg-white text-gray-900 transition-colors duration-250 shadow-md outline-none cursor-pointer hover:border-blue-500 active:border-blue-500 active:bg-gray-200 dark:bg-gray-900/60 dark:text-white dark:active:bg-gray-900/40"
      >
        Greet
      </button>
    </form>
    <p class="mt-4">{{ greetMsg }}</p>
  </main>
</template>

