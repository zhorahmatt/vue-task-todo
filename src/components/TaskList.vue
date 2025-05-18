<script lang="ts" setup>
import type { Task } from '../types';

const props = defineProps<{
    tasks: Task[]
}>();

const emits = defineEmits<{
    toggleDone: [id: string];
    removeTask: [id: string];
}>();
</script>
<template>
    <TransitionGroup name="list" tag="div" class="task-list">
        <article v-for="task in props.tasks" :key="task.id" class="task">
            <label for="">
                <input 
                    @input="emits('toggleDone', task.id)"
                    type="checkbox"
                    :checked="task.done"
                >
                <span :class="{ done: task.done }">
                    {{ task.title }}
                </span>
            </label>
            <button @click="emits('removeTask', task.id)" class="outline">Remove</button>
        </article>
    </TransitionGroup>
</template>

<style>
.task-list {
    margin-top: 1rem;
}

.done {
    text-decoration: line-through;
}

.task {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(300px);
}
</style>