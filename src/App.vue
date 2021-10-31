<script setup>
import { ref, computed } from "vue"

const newTodo = ref("");

const todos = ref([]);

const pending = computed(() => {
  return todos.value.filter((todo) => !todo.done);
});

const completed = computed(() => {
  return todos.value.filter((todo) => todo.done);
});

const addTodo = () => {
  if(newTodo.value.trim()) {
    todos.value.push ({
    id: todos.value.length,
    content: newTodo.value,
    done: false,
    });
    newTodo.value = "";
  }

};

const changeStatus = (id) => {
  const todo = todos.value.find((todo) => todo.id === id);
  todo.done = !todo.done;
};

</script>

<template>
<div class = "min-h-screen bg-gray-400">
  <div class = "container flex flex-col pt-8 mx-auto space-y-8">
 <h1 class = "text-6xl font-thin tracking-tight text-center text-gray-300">🚀 My ToDo App!</h1>
 <input
  @change = "addTodo"
  v-model = "newTodo" type="text" class="px-4 py-2 text-center rounded-lg py-xl" placeholder="New Item"/>
 <div class = "flex justify-around">
   <div class = "w-1/3">
   <h3 class = "text-2xl text-center text-blue-800">Pending:</h3>
   <ul class = "pt-8 space-y-4">
     
     <li
     v-for = "todo in pending"
     :key = "todo.id"
     @click = "changeStatus(todo.id)"
      class="w-full px-4 py-2 font-bold text-center text-white duration-500 bg-yellow-500 rounded-lg cursor-pointer hover: hover:bg-black hover:text-red-600">{{todo.content}}</li>
     

   </ul>
 </div>
  <div class = "w-1/3">
   <h3 class = "text-2xl text-center text-purple-900">Completed:</h3>
   <ul class = "pt-8 space-y-4">
     <li 
    v-for = "todo in completed"
    :key = "todo.id"
    @click = "changeStatus(todo.id)"
     class="w-full px-4 py-2 font-bold text-center text-white duration-500 bg-black rounded-lg cursor-pointer hover: hover:bg-gray-300 hover:text-pink-600">{{todo.content}}</li>

   </ul>
 </div>
 </div>
 </div>
 </div>
</template>
