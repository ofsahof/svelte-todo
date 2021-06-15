<script lang="ts">
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  import type { TODO } from "../types";
  export let todos: TODO[];
  let text = "";

  function addTodo() {
    if (text) {
      dispatch("add", { txt: text });
      text = "";
    }
  }
</script>

<div>
  <input
    placeholder="Yapılacak bir iş girin"
    type="text"
    on:keydown={(event) => {
      event.key === "Enter" ? addTodo() : null;
    }}
    bind:value={text}
  />
  <button on:click={addTodo}>Add</button>
</div>

<style>
  input {
    width: 220px;
    height: 35px;
    border-radius: 14px;
    padding: 5px 10px;
    border: 1px solid transparent;
    box-shadow: 1.5px 1.5px 1px 1px gray;
    outline: none;
  }

  button {
    display: block;
    width: 80px;
    height: 40px;
    padding: 5px 10px;
    border-radius: 14px;
    cursor: pointer;
    outline: none;
    margin-top: 10px;
    transition: 0.25s all;
  }

  button:hover {
    background-color: rgba(215, 215, 215, 1);
    /* font-size: 1.25em; */
    transform: scale(1.1);
  }
</style>
