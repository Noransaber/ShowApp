<script setup>
import axios from "axios";
import { ref, watch } from "vue";
import Card from './cards.vue'

const characters = ref(null)
const page = ref(0);
//because i will send the request and the response will be sent back and will be saved in this var
const response = await axios.get("https://thronesapi.com/api/v2/Characters?limit=8");
characters.value = response.data
watch(page, async () => {
    //here we watch the changes of page, whenever it changes multi * with new changes to get new characters
    const response = await axios.get(`https://thronesapi.com/api/v2/Characters?limit=8$offset=${page.value * 8}`);
    // update the value to the data come from res
    characters.value = response.data
// here that will not work because the api itself doen't support limit and offset.i just wrote it for learning
})
console.log(response)
</script>


<template>
        <div class="container">
            <div class="cards">
                <Card 
                    v-for="character in characters"
                    :key='character.id'
                    :name='character.fullName'
                    :image='character.imageUrl'
                  
                    >
                    <div class="jobs">
                        <p v-for='(family,index) in character.family' :key='family'>  {{ family }} <span v-if="index < character.family.length - 1">,&nbsp</span></p>
                    </div>                
                </Card>

            </div>
            
        </div>
</template>

<style scoped>
.container {
    background-color: rgb(27, 26, 26);
    padding: 30px
}
.cards {
    max-width: 1000px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    height: 700px
}
.cards h3 {
    font-weight: bold;
}
.cards p {
    font-size: 10px;
}

.button-container {
    display: flex;
    justify-content: center;
    padding-top: 30px
}
.button-container button {
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 100%;
    margin: 0 5px;
    cursor: pointer;
}
.spinner {
    display: flex;
    align-items: center;
    justify-content: center;
}

p {
    font-size: 10px;
}

.jobs {
    display: flex;
    flex-wrap: wrap;
}

</style>