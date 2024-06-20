<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />

  <div class="bg-white shadow-md p-4 rounded-md">
    <input type="text" class="w-full px-3 py-2 rounded-md border focus:outline-none focus:ring focus:border-blue-300"
      v-model="inputValue" @input="handleChange" />
    <ul v-if="filteredOptions.length > 0" class="mt-1">
      <li v-for="option in filteredOptions" :key="option" class="py-1 px-3 cursor-pointer hover:bg-gray-100">{{ option
        }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputValue: '',
      options: ['Apple', 'Banana', 'Cherry', 'Date'],
    };
  },
  computed: {
    filteredOptions() {
      return this.options.filter(option =>
        option.toLowerCase().includes(this.inputValue.toLowerCase())
      );
    },
  },
  methods: {
    handleChange(event) {
      this.inputValue = event.target.value;
    },
  },
};
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
