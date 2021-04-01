<script lang="ts">
    import {todos} from "../todoStore.js"

    const addTodo = (title) => {
        const length = 32;

        const newTodo = {
            id: Math.round(
                Math.pow(36, length + 1) - Math.random() * Math.pow(36, length)
            )
                .toString(36)
                .slice(1),
            title,
            completed: false,
        };

        todos.update(all => {
            return [...all, newTodo]
        });
    };


    let title = '';

    const onSubmit = (e) => {
        e.preventDefault();
        addTodo(title);
        title = '';
    }

    const handleChange = (e) => {
        title = e.target.value;
    }
</script>

<main>
    <div>
        <form on:submit={onSubmit} class="flex">
            <input
                    type='text'
                    name='title'
                    class="flex-10"
                    placeholder='Add Todo ...'
                    bind:value={title}
                    on:change={handleChange}
            />
            <input
                    value='Submit'
                    type='submit'
                    className='btn'
                    class="flex-1"
            />
        </form>
    </div>
</main>

<style lang="scss">
  .flex-10 {
    flex: 10;
    padding: 5px;
  }
</style>