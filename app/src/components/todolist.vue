<template>
  <div style="padding-top: 70px;">
    <input class="addTODOSINPUT" type="text" v-model="NewTodo"  @keydown.enter="add" :placeholder="'To dos: ' + todosinlist ">
    <table id="tabel">
        <tr v-for="todo in Todo" :key="todo.id">
            <td>
                <input class="checkbox" type="checkbox"  @click="Delet(todo.id)">
                <i>
                    {{ todo.text }}
                </i>
            </td>
        </tr>
    </table>
  </div>
</template>

<script>
export default {
    name:"ToDo List",
    data(){
        return{
            NewTodo:"",
            Todo:[],
            todosinlist: 0
        }
    },
    methods:{
        add(){
            this.todosinlist += 1
            this.Todo.push({ text: this.NewTodo,id:this.todosinlist});
            this.NewTodo = "";
        },
        Delet(id){
            this.todosinlist -= 1
            this.Todo = this.Todo.filter(todo => todo.id !== id);
        }
    }
}
</script>

<style>
    body{
        background-image: url("C:\Users\plate\OneDrive\Dokumente\dev\ToDo List\app\src\assets\pexels-jaime-reimer-2662116.jpg");
        background-size: 100%;
        display: flex;
        justify-content: center;
        font-family: Arial, Helvetica, sans-serif;
        font-size: medium;
    }
    .addTODOSINPUT{
        border: none;
        border-radius: 10px;
        height: 30px;
        width: 600px;
        padding-left: 10px;
    }
    .checkbox{
        height: 20px;
        width: 40px;
    }
    table{
        padding-top: 10px;
        padding-left: 10px;
    }
    table tr td i{
        color: aliceblue;
        padding-left: 200px;
    }
</style>