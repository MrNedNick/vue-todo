<template>
    <div class="main"> 
        <h2>Vue Todo App</h2>

        <!-- input -->
        <div >
            <input class="input" @keyup.enter="submitTask" v-model="task" type="text" placeholder="Enter task">
            <button class="submit" @click="submitTask" >SUBMIT</button>
        </div>

        <!-- LIST -->
        <div class="list" v-for="(task, index) in tasks" :key='index'>
            <div class="list__item">
                <div class='item__name'>{{ task.name }}</div>
                <div class="item__edit">
                    <div class="edit__item" @click="editTask(index)">
                        <span class="fa fa-pen"></span>
                    </div>
                    <input class="edit__item" type="checkbox">
                    <div class="edit__item" @click="deleteTask(index)">
                        <span class="fa fa-trash"></span>
                    </div>
                </div>
            </div>
        </div>
        
    </div>
</template>

<script>
export default {
    name: 'Header',

    data(){
        return {
            task: '',
            editedTask: null,
            tasks: [
                {
                    name: 'Clean my room',
                },
                {
                    name: 'Read new book',
                }
            ]
        }
    },

    methods: {
        submitTask(){
            if(this.task.length === 0) return;

            if(this.editedTask === null){
                this.tasks.push({
                    name: this.task,
                    status: 'to-do'
                })
            }else{
                this.tasks[this.editedTask].name = this.task
                this.editedTask = null
            }

            this.task = ''
        },

        deleteTask(index){
            this.tasks.splice(index, 1)
        },

        editTask(index){
            this.task = this.tasks[index].name
            this.editedTask = index
        }
    }
}


</script>

<style scoped>
.main{
    display: flex;
    flex-direction: column;
    align-items: center;
}
.input{
    height: 24px;
    width: 300px;
}
.submit {
    width: 100px;
    height: 30px;
    border-color: rgb(238, 223, 196);
    background-color: rgb(230, 236, 177);
    font-weight: 700;
}
.list__item {
    display: flex;
    justify-content: space-between;
    width: 400px;
    margin: 10px;
}
.item__name {
    
}
.item__edit {
    display: flex;
}
.edit__item{
    margin-right: 10px;
}
</style>

