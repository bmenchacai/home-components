<script setup>
import Main from './components/Main.vue'
</script>

<template>

  <Main msg="Vue" />

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
