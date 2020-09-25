<template>
    <div>
        <h1>Task List</h1>
        <ul>
            <li v-for="t in tasks" v-bind:key="t.id">
                {{t.name}} -- <input type="checkbox" v-model="t.done"/>
                <button @click="deleteTask(t)">Delete</button>
            </li>
        </ul>
        <div>
            <label>Task Name:</label>
            <input type="text" v-model="newTaskName"/>
            <button @click="add">Add</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "TaskList",
    data: function(){
        return {
            tasks: [
                {
                    id: 1,
                    name:'Walk the dog',
                    done:false
                },
                {
                    id: 2,
                    name:"Pay the bills",
                    done: true
                },
                {
                    id: 3,
                    name:"Wash the Car",
                    done: false
                }
            ],
            newTaskName:""
        }
    },
    methods:{
        add:function(){
            this.tasks.push({
                id: Math.floor(Math.random() * 10000 + 99999),
                name: this.newTaskName,
                done:false
            })
        },
        deleteTask:function(toDelete){  
            let index = this.tasks.indexOf(toDelete);
            this.tasks.splice(index, 1)

        }
    }
}
</script>

<style>
</style>