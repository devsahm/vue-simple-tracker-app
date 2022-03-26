<template>
    <div>
        <form class="add-form" action="" @submit="onSubmit">
            <div class="form-control">
                <label for="">Add task</label>
                <input type="text" v-model="text" name="text" placeholder="Add Task">
            </div>
            
            <div class="form-control">
                <label for="">Day and Time</label>
                <input type="text" v-model="day" name="day" placeholder="Day and Time">
            </div>

               <div class="form-control form-control-check">
                <label>Set Reminder</label>
                <input type="checkbox" v-model="reminder" name="reminder" placeholder="Add Task">
            </div>

            <input type="submit" value="Add Task"  class="btn btn-block">

            

        </form>
    </div>
</template>

<script>
export default {
    name: 'AddTask',

    data(){
        return{
            text:'',
            day:'',
            reminder:false
        }
    },
    methods:{

        onSubmit(e){
            e.preventDefault();

            if (!this.text) {
                alert('The text is required');
                return
            }

            const newTask = {
                id:Math.floor(Math.random() * 10000),
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }

            this.$emit('add-task', newTask);

            this.text= '',
            this.day= '',
            this.reminder= false
        }
    }
}
</script>

<style scoped>
.add-form{
    margin-bottom: 40px;
}

.add-form input{
    width: 100%;
}

.form-control{
    margin: 20px 0;
}

.form-control label{
    display: block;
}

.form-control input{
    height: 40px;
    width: 100%;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
}

.form-control-check{
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.form-control-check label{
    flex: 1;
}

.form-control-check input{
    flex: 2;
    height: 20px;
}

</style>