<template>
 <!--Using double click event we toggle the reminder(We switch the reminder to true/false) --> 
 <!--Based on the condition of reminder we change the color of label of tasks!-->
 <!--Also there is delete event where we have font awesome-->
 <div 
 @dblclick="$emit('toggle-reminder', task.id)"
 :class='[task.reminder ? "reminder" : "", "task"]'>
    <h3> 
        {{task.text}} 
    <i @click="$emit('delete-task',task.id)" class="fas fa-times"></i>
    </h3>
 </div>
</template>

<script>
export default {
    name: "Task",
    // Here is a prop called task is required, and basically its an Object!
    props: {
        task: Object
    }
}
</script>

<style scoped>
.fas {
    color: red;
}

.task {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}

.task.reminder {
    border-left: 5px solid green;
}

.task h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>