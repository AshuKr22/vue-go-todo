<script setup lang="ts">
import { reactive, ref } from 'vue';
import ToDoList from './components/ToDoList.vue';
//pre exisiting todos array
const todos = reactive([{id:1 , task:"do the dishes", done:true}])
//use state for a new todo
const newTask = ref('');
//add todo function
const addTodo = ()=>
{
  if(newTask.value.trim()!=="")
  {
    todos.push({
      id:todos.length+1,
      task: newTask.value,
      done: false
    })
    console.log(todos);
    
    newTask.value=''

  }
}
</script>

<template>
 <div class="flex flex-col justify-center items-center h-full w-full">
  <h1 class="text-3xl mt-3">To Do List 📃</h1>
 
    <form action="" @submit.prevent="addTodo" class="flex flex-row justify-center items-center gap-2 w-full">
  <input type="text" name="" id="" v-model="newTask" class="input input-bordered w-full max-w-xl my-4 p-2">
    <button class="btn" type="submit">add</button>
  </form>

  <ToDoList  :items="todos"/>
 </div>
</template>


