<script setup lang="ts">
import ToDoItem, { IToDoItem } from './ToDoItem.vue';

// Define props
const props =defineProps<{
  items: IToDoItem[]; 
}>();

// Create a local reactive copy of `items`

const toggleDone = (id: number) => {
  const item = props.items.find((i) => i.id === id);
  if (item) {
    item.done = !item.done;
  }
};
//filter didnt work had to use slice 
const deleteItem = (id: number) => {
  const index = props.items.findIndex((i) => i.id === id);
  if (index !== -1) {
    props.items.splice(index, 1);
  }
};

</script>

<template>
    <div class=" w-full flex flex-col items-center mx-auto overflow-y-auto">
      <div class="space-y-2 overflow-auto h-full">
      <ToDoItem
        v-for="item in props.items"
        :key="item.id"
        :id="item.id"
        :task="item.task"
        :done="item.done"
        @toggle-done="toggleDone"
        @delete-item="deleteItem"
      />

    </div>
  </div>
</template>