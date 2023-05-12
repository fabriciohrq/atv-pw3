<template>
    <div class="add-task">
        <template v-if="tasks.length">
            <TaskItem 
                v-for="(task, i) in tasks" 
                :key="i" 
                :task="task"
                @taskDeleted="$emit('taskDeleted', i)"
                @taskStateChanged="$emit('taskStateChanged', i)"
            />
        </template>
        <p v-else class="no-task">Sua vida está em dia!</p>
    </div>
</template>

<script>
import TaskItem from './TaskItem.vue';
export default {
    name: 'add-task',
    components: {
        TaskItem
    },
    props: {
        tasks: {
            type: Array,
            required: true
        }
    }
}
</script>

<style>
    .task-grid{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        gap: 20px;
    }

    .task{
        margin: 10px;
    }

    no-task{
        font-size: 1.7rem;
    }
</style>