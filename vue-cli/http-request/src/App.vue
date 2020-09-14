<template>
  <div id="container">
    <div class="row">
      <div class="col-md-8 offset-md-2 text-center">
        <h3 class="mt-5">ToDo List</h3>
        <hr>
        <div class="row">
          <div class="col-md-6 offset-md-3 d-flex flex-row justify-content-between align-items-center">
            <input type="text" v-model="toDoText">
            <button @click="addToDo()" class="btn btn-primary">Ekle</button>
          </div>
        </div>
        <hr>
        <div class="todo-container">
          <Todo v-for="todo in toDoList" :key="todo.id" :todo="todo" @deletetodo="deleteToDo($event)" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "@/components/Todo"
import axios from "axios"
export default {
  components: {
    Todo
  },
  data(){
    return {
      toDoText: "",
      toDoList: []
    };
  },
  methods: {
    addToDo(){
      axios.post("https://vuejs-http-request-7bb50.firebaseio.com/todos.json", { text: this.toDoText })
        .then(response => {
          console.log(response);
          this.toDoList.push({
            id: response.data.name,
            text: this.toDoText
          });
        })
        .catch(e => {
          console.log(e);
        })
    },
    deleteToDo(todoId){
      axios.delete("https://vuejs-http-request-7bb50.firebaseio.com/todos/" + todoId + ".json")
        .then(response => {
          let index = this.toDoList.findIndex(i => {
              return i.id == todoId;
          });
          this.toDoList.splice(index, 1);
        })
        .catch(e => {
          console.log(e);
        })
    }
  },
  created() {
    axios.get("https://vuejs-http-request-7bb50.firebaseio.com/todos.json")
      .then(response => {
        console.log(response.data);
        for(let key in response.data){
          console.log(response.data[key]);
          let todo = {
            id: key,
            text: response.data[key].text
          };
          this.toDoList.push(todo);
        }
      })
      .catch(e => {
        console.log(e);
      })
  }
}
</script>

<style>

</style>
