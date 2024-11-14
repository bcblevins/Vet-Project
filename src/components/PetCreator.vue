<template>
    <div>
        <h1 class="message"> {{ message }} </h1>
        <h2> {{ name }} </h2>
        <h2> {{ species }} </h2>
        <h2> {{ breed }} </h2>
        <h2> {{ color }} </h2>
        <h2> {{ birthday }} </h2>
        <form @submit.prevent="">
            <input type="text" v-model="input">
            <button @click="saveInfo">save</button>
        </form>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const message = ref("Hello");
const input = ref("");
const index = ref(0);

const species = ref("");
const name = ref("");
const breed = ref("");
const color = ref("");
const birthday = ref("");

const details = [species, name, breed, color, birthday];

const saveInfo = () => {
    console.log(details.value)
    details[index.value].value = input.value;
    input.value = "";
    index.value++;
    changeMessage();
}

const changeMessage = () => {
    switch (index.value) {
        case 0:
            message.value = "What kind of pet do you have?"
            break;
        case 1:
            message.value = `What is your ${species.value}'s name?`
            break;
        case 2:
            message.value = `What is ${name.value}'s breed?`
            break;
        case 3:
            message.value = `What color is ${name.value}?`
            break;
        case 4:
            message.value = `What is ${name.value}'s birthday?`
            break;
    }
}


// @mounted
changeMessage();

</script>

<style lang="scss" scoped></style>