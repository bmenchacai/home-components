<template>
  <Temp />

  {{ msg }}

</template>

<script setup>
import { ref } from 'vue'
import Temp from './Temp.vue'

defineProps({
  msg: String,
})

</script>
