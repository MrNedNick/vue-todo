<template>
    <div> 
        <h2>Vue Todo App</h2>

        <!-- input -->
        <div>
            <input @keyup.enter="submitTask" v-model="task" type="text" placeholder="Enter task">
            <button @click="submitTask" >SUBMIT</button>
        </div>

        <!-- TABLE -->
        <table>
            <thead>
                <tr>
                    <th>Task</th>
                    <th>#</th>
                    <th>#</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(task, index) in tasks" :key='index'>
                    <th>{{ task.name }}</th>
                    <th>
                        <div @click="editTask(index)">
                            <span class="fa fa-pen"></span>
                        </div>
                    </th>
                    <th>
                        <div @click="deleteTask(index)">
                            <span class="fa fa-trash"></span>
                        </div>
                    </th>
                </tr>
            </tbody>
        </table>

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

