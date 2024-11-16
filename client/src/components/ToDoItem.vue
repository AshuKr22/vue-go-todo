<script setup lang="ts">

defineProps({
    id: {type: Number, required:true, 
    },
    task: {type: String },
    done : {type: Boolean, default:false},


})

defineEmits(['toggle-done','delete-item']);
    
export type IToDoItem = {
  id: number;
  task: string
  done: boolean;
};
</script>

<template>

    <div class="text-2xl my-2 flex flex-row gap-2 w-[50vw] bg-slate-800 p-4 rounded-md justify-between ">
        <span>{{ task }}</span>
        <div class="self-end flex flex-row gap-1">
        <div @click="$emit('toggle-done',id)" class=" cursor-pointer">
         <div v-if="done">✅</div>
         <div v-else>❌</div>
        </div>
        <button class="ml-2" @click="$emit('delete-item',id)">
            🗑️
        </button>
    </div>
    </div>

</template>
