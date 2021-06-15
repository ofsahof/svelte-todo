<script lang="ts">
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  import type { TODO } from "../types";
  export let todos: TODO[];
  let text = '';

  function addTodo() {
      dispatch('add',{txt: text});
      text = "";
  }
</script>

<div>
  <input type="text" on:keydown={(event) => {event.key === "Enter" ? addTodo() : null}} bind:value={text} />
  <button on:click={addTodo}>Add</button>
</div>
