<script lang="ts">
    import type {TODO} from "../types";
    export let todos: TODO[];

    function removeItem(index: number) {
        todos.splice(index, 1);
        todos = todos;
    }
</script>

<ul>
    {#each todos as item,index}
        <li>
            <input bind:checked={item.isChecked} type="checkbox">
            <span class={item.isChecked ? 'lined' : ''}>{item.text}</span>
            <span class="icon" on:click={() => removeItem(index)}>❌</span>
        </li>
    {/each}
</ul>

<style>
    ul {
        list-style:none;
        margin-top: 7.5px;
    }
    .lined {
        text-decoration: line-through;
    }
    .icon {
        cursor: pointer;
    }
</style>