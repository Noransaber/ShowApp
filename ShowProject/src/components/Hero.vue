<script setup >
import { defineProps, defineEmits } from "vue"

const emitselcetedShow = () => {
    emit("selcetedShow")
}

const {isGameOfThrones} = defineProps([
    'isGameOfThrones'
])
const emit = defineEmits(['selcetedShow'])


</script>

<template>
    <div class="hero">
        <h1>{{ isGameOfThrones ? 'Game Of Thrones' :  'Ricky and Morty' }} </h1>
        <p @click='emitselcetedShow'>{{ isGameOfThrones ? 'Ricky and Morty' :  'Game Of Thrones' }} </p>
    </div>
</template>

<style scoped>
.hero {
    height : 40vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    flex-direction: column
}
.hero img {
    position: absolute;
    height: 700px;
    opacity: 0.1;
}
.hero h1 {
    font-size: 100px;
    font-weight: bold;
}
.hero p {
    cursor: pointer;
}
</style>