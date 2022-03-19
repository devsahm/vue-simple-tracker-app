<template>
    <div @dblclick="$emit('toogle-reminder', task.id)" :class="['task', task.reminder? 'reminder':'']">
    <h3>{{ task.text }} 

    <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i> 

    </h3>
    <p>{{ task.day }}</p>
    </div>
</template>


<script>
export default {
    name:'Task',
    props:{
        task: Object
        
    },
   
}
</script>


<style scoped>

.fas{
    color: red;
}
.task {
    background: #f4f4f4;
    margin: 5px;
    padding: 5px 15px;
    cursor: pointer;
}

.task.reminder {
    border-left: 5px solid green;
}

.task h3{
    display: flex;
    align-items: center;
    justify-content: space-between;

}
</style>