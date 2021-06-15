<script lang="ts">
  import type { TODO } from "./types";
  import TodoApp from "./lib/TodoList.svelte";
  import TodoButtons from "./lib/TodoButtons.svelte";

  let todoList: TODO[] = JSON.parse(localStorage.getItem("todos")) || [];

  $: {
    localStorage.setItem("todos", JSON.stringify(todoList));
  }
</script>

<main>
  <TodoButtons
    on:add={(event) => {
      todoList.push({ text: event.detail.txt, isChecked: false });
      todoList = todoList;
    }}
    on:clear={(event) => {
      todoList = [];
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
