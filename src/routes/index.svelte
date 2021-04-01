<script lang="ts">
    import Input from "../lib/Input.svelte";
    import Todos from "../lib/Todos.svelte";
</script>

<main class="bg-gray-900 h-screen">
    <Input />
    <Todos />
</main>

<style global lang="postcss">
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
</style>