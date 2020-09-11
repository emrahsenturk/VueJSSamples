<template>
  <div id="container">
    <div class="row">
      <div class="col-md-8 offset-md-2 text-center">
        <h3 class="mt-5">ToDo List</h3>
        <hr>
        <div class="row">
          <div class="col-md-6 offset-md-3 d-flex flex-row justify-content-between align-items-center">
            <input type="text">
            <button class="btn btn-primary">Ekle</button>
          </div>
        </div>
        <hr>
        <div class="todo-container">
          <Todo />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "@/components/Todo"
export default {
  components: {
    Todo
  }
}
</script>

<style>

</style>
