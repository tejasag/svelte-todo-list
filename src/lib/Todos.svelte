<script lang="ts">
    import {todos} from "../todoStore.js";
    import TodoItem from "./TodoItem.svelte";
    import {onDestroy} from "svelte";

    let data = []
    const uns = todos.subscribe(value => {
        data = value
    })

    onDestroy(uns)
</script>

<main>
    {#if data.length === 0}
        <h1 class="text-white">No Tasks found</h1>
    {:else}
        {#each data as todo}
            <TodoItem todo={todo}/>
        {/each}
    {/if}
</main>