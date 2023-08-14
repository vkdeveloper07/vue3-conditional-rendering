<template>
    <div class="buttonsContainer">
        <button :class="[vIfDemo ?'selectedTemplate' : 'unselectedTemplate']" @click="vIfDemoToggle">v-If Demo</button>
        <button :class="[vElseIfDemo ?'selectedTemplate' : 'unselectedTemplate']" @click="vElseIfDemoToggle">v-else-If Demo</button>
        <button :class="[vElseDemo ?'selectedTemplate' : 'unselectedTemplate']" @click="vElseDemoToggle">v-else Demo</button>
    </div>
    
    <template v-if="vIfDemo">
        <div class="container">
            <h1>v-if demo</h1>
            <h2 v-if="isTasteGood">Food is good</h2>
            <h2 v-else>Food is not good</h2>
        <button @click="toggleState">Toggle food taste</button>
    </div>
    </template>

    <template v-else-if="vElseIfDemo">
        <div class="container">
            <h1>V-else-if demo</h1>
            <h2 v-if="selectedValue === 'A'">A is true</h2>
            <h2 v-else-if="selectedValue === 'B'">B is true </h2>
            <h2 v-else-if="selectedValue === 'C'">C is true</h2>
            <select v-model="selectedValue">
                <option value="A">A</option>
                <option value="B">B</option>
                <option value="C">C</option>
            </select>
        </div>
    </template>

    <template v-else="vElseDemo">
        <div class="container">
            <h1>Template v-else is shown after all other v if and v-else if are false</h1>
        </div>
    </template>
</template>

<script setup>
import { ref } from 'vue';
let isTasteGood = ref(true);
let vIfDemo = ref(true);
let vElseIfDemo = ref(false);
let vElseDemo = ref(false);

let selectedValue = ref('');

// button click functions start

function vIfDemoToggle(){
    vIfDemo.value = true;
    vElseIfDemo.value = false;
    vElseDemo.value = false;
}

function vElseIfDemoToggle(){
    vIfDemo.value = false;
    vElseIfDemo.value = true;
    vElseDemo.value = false;
}

function vElseDemoToggle(){
    vIfDemo.value = false;
    vElseIfDemo.value = false;
    vElseDemo.value = true;
}

// button click functions end

function toggleState(){
    isTasteGood.value = !isTasteGood.value
}

</script>

<style scoped>
.container{
    text-align: center;
    width: 100%;
    border: 2px solid white;
}
button{
    border-radius: 5px;
    height: 25px;
}
.buttonsContainer button{
    margin:5px;
    height: 30px;
    border-radius: 10px;
}
.selectedTemplate{
    background-color: green;
}
.unselectedTemplate{
    background-color: red;
}
</style>