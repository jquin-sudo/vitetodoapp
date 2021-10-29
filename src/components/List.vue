<script setup>
import useTodos from "../composables/useTodos";

const { pending, completed, changeStatus } = useTodos();

defineProps({
  isCompleted: {
    default: false,
    type: Boolean,
  },
});
</script>

<template>
  <div class="w-1/3">
    <h3
      class="text-2xl text-center bg-yellow-700 rounded-lg"
      :class="isCompleted ? 'text-white' : 'text-white'"
    >
      {{ isCompleted ? "Completed" : "Pending" }}
    </h3>
    <ul class="pt-8 space-y-4">
      <li
        v-for="todo in isCompleted ? completed : pending"
        :key="todo.id"
        @click="changeStatus(todo.id)"
        :class="
          isCompleted
            ? 'text-black hover:bg-yellow-700'
            : 'text-black hover:bg-yellow-700'
        "
        class="w-full px-4 py-2 font-bold text-center transition-colors  bg-yellow-300 rounded-lg  hover:cursor-pointer hover:text-white"
      >
        {{ todo.content }}
      </li>
    </ul>
  </div>
</template>
