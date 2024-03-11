<template lang="">
    <!-- <div class="My-Profile">
        <p class="text-bg-dark">My name is {{ name }}</p>
        <p>I'm {{ age }} years old</p>
        <p>My position {{ position }}</p>
        <button @click="count++">{{count}}</button><br>
        <input v-model="name" placeholder="edit name">
        <p>My favourite programming language is</p>
        <p v-for="myCode in myCodes">{{ myCode.name }}</p>
        <p v-for="myCode in myCodes">{{ myCode.name }}</p>
        <p v-for="myCode in myCodes">{{ myCode.name }}</p>
    </div> -->
    <main class="cardTodo">
        <div class="bg-light text-center shadow rounded-3 todolist pb-1">
            <H1>{{title}}</H1>
            <div class="input-group p-2">
                <input v-model="newTask" class="form-control" placeholder="What do you do?">
                <button class="btn btn-outline-secondary" @click="addTask" :disabled="newTask.length < 1">Add task</button>
            </div>
            <div v-for="task in tasks" class="d-flex justify-content-between p-2 m-2 rounded-3 shadow-1 fs-6"
                :class="task.finished ? 'bg-success':'bg-secondary'"
            >
                <div class="my-auto" :class="task.finished ? 'text-dark' : 'text-light'">{{task.name}}</div>
                <div class="btn-group" role="group" aria-label="">
                    <button type="button" class="btn btn-success" @click="task.finished = !task.finished">Finished</button>
                    <button type="button" class="btn btn-danger" @click="removeTask(task.name)">Delete</button>
                </div>
                <div v-if="task.finished" class="DoneIT">DONE IT</div>
            </div>
        </div>
    </main>
</template>
<script>
export default {
    data(){
        return {
            title:"My To Do List",
            tasks:[
                { name:"Learn Vue.js" , finished:false },
                { name:"Learn Vue.js NavBar" , finished:false },
                { name:"Learn Vue.js To Do List" , finished:false },
                { name:"Learn Vue.js CRUD" , finished:false },
            ],
            newTask:'',
        }
    },
    methods: {
        addTask(){
            this.tasks.push({
                name: this.newTask,
                finished:false,
            });
            this.newTask = '';
        },
        removeTask(TaskName){
            this.tasks =this.tasks.filter(task => {
                return task.name !== TaskName
            })
        }
    },
}
</script>
<style scoped>
    .My-Profile {
        color:blue;
        text-align: center;
        /* background-color: yellow; */
        border-radius: 0.5rem;
        filter: drop-shadow(0 2px 4px rgb(0 0 0 / 0.1))
    }
    .todolist {
        width: 800px;
        margin: auto;
    }
    .cardTodo {
        background-color: #FFE6D4;
        width: 100%;
        min-height: 100vh;
        padding-top: 3rem ;
        padding-bottom: 1rem;
    }
    .DoneIT{
        position: absolute;
        left: 50%;
        transform: translate(-50%, 0);
        font-size: 1.5rem;
        font-style: italic;
        font-weight: 900;
        color: white;
    }
</style>