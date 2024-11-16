<script setup lang="ts">
import { onMounted, reactive, ref } from 'vue';
import ToDoList from './components/ToDoList.vue';
//pre exisiting todos array

const todos = reactive([{id:1 , task:"do the dishes", done:true}])
onMounted(()=>{
  for(let i=0;i<10;i++)
{
  todos.push({
    id: todos.length+1,
    task: "sample task "+todos.length,
    done: false
  })

}
})
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
  <div class="min-h-screen flex flex-col p-4">
    <h1 class="text-3xl text-center mb-6">To Do List 📃</h1>
    
    <div class="w-full max-w-2xl mx-auto flex-none">
      <form @submit.prevent="addTodo" class="flex gap-2 mb-6">
        <input 
          type="text" 
          v-model="newTask" 
          class="input input-bordered flex-grow p-2"
          placeholder="Add a new task..."
        >
        <button class="btn" type="submit">Add</button>
      </form>
    </div>

    <div class="flex-grow overflow-auto ">
      <ToDoList :items="todos" />
    </div>
  </div>
</template>

