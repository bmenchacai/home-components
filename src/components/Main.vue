<template>

  <!-- {{ msg }} -->
  <!-- <Practice/> -->
  <!-- <Tooltip/> -->
  <!-- <Test/> -->
<h1>Bder</h1>
</template>

<script setup>
import { ref } from 'vue';
import Test from './Test.vue';
import Tooltip from './Tooltip.vue';

defineProps({
  msg: String,
})

</script>