<template>
  <Temp />
  <Shuffle />

  {{ msg }}

</template>

<script setup>
import { ref } from 'vue';
import Temp from './Temp.vue';
import Shuffle from './Shuffle.vue';

defineProps({
  msg: String,
})

</script>
