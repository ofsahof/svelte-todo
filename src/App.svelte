<script lang="ts">
  import type { TODO } from "./types";
  import TodoApp from "./lib/TodoList.svelte";
  import CreateTodo from "./lib/CreateTodo.svelte";

  let todoList: TODO[] = JSON.parse(localStorage.getItem("todos")) || [];

  $: {
    localStorage.setItem("todos", JSON.stringify(todoList));
  }
</script>

<main>
  <CreateTodo
    on:add={(event) => {
      todoList.push({ text: event.detail.txt, isChecked: false });
      todoList = todoList;
    }}
    bind:todos={todoList}
  />
  <TodoApp bind:todos={todoList} />
</main>

<style>
  main {
    margin-top: 25px;
  }
</style>
