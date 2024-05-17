<template>
    <div class="page-container">
        <div class="container">
            <div class="row">
                <div class="column column-left">
                    <div>
                        TO DO
                    </div>
                    <div>
                        <input v-model="inputBox">
                    </div>
                    <div @click="addTodo()" >
                        <button class="add-button">Add</button>
                    </div>
                </div>
                <div v-if="list.length >= 1" class="column column-right">
                    <div>
                        {{ list }}
                    </div>
                    <div>
                        LIST:
                    </div>
                        <div class="row list" v-for="(todo, idx) in list" :key="idx">
                        <button class="delete-button" @click="deleteTodo(idx)"> Delete </button>
                        {{ todo }} - {{  idx }}
                    </div>      
                </div>
            </div>

        </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'


const inputBox = ref(null)
const list = ref([])

function addTodo(){
    if (!inputBox.value) return
    list.value.push(inputBox.value)
    inputBox.value = null
}

function deleteTodo(index: number){
    list.value.splice(index, 1)
}
</script>

<style scoped>
.page-container {
    display: flex;
    justify-content: center;
    align-content: center;
}

.container {
    text-align: center;
    width: 80vw;
    /* background-color: red; */
    padding: 10px;
}

.row {
    width: 100%;
    display: flex;
    justify-content: center;
}

.column {
    width: 50%;
    border: 1px solid white;
    padding: 10px;
}
.column-right {
    width: 30%;
}
.column-left {
    width: 70%;
}

.list {
    justify-content: start;
}

.add-button{
    background-color: green;
    color: white;
    width: 80px;
    margin-top: 10px;
}
.delete-button{
    background-color: red;
    color: white;
    width: 80px;
    margin-right: 20px;
    margin-top: 5px
}

</style>
