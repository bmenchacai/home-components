<template>

    <h1 class="font-bold">My course</h1>
    <p>{{ courseGoal }}</p>
    <p>Lean more <a v-bind:href="vueLink">about Vue</a></p>
    <b>{{outputGoal()}}</b>

</template>

<script>
import { ref } from 'vue';

export default {
    components: {
    },
    props: {
    },
    data() {
        return {
            courseGoal: 'Finish the course and learn Vue!',
            vueLink: 'https://vuejs.org/'
        };
    },
    computed: {
    },
    methods: {
        outputGoal() {
            const randomNumber = Math.random();
            if(randomNumber < 0.5) {
                return 'Learn vue!';
            } else {
                return 'Master Vue!';
            }
        }
    },
    mounted() {
    },
    destroyed() {
    },
    beforeDestroy() {
    },
    created() {
    },
    toggleDisabled() {
    },
    showAdvice() {
    }
};


</script>