<script lang="ts">
    import {todos} from "../todoStore.js";

    interface todoI {
        title: String,
        id: String,
        completed: Boolean
    }

    const markComplete = (id) => {
        todos.update(all => {
            return all.map(todo => {
                if (todo.id === id) {
                    todo.completed = !todo.completed
                }
                return todo
            })
        })
    };

    const delTodo = (id) => {
        todos.update(
            all => {
                return all.filter((todo) => todo.id !== id)
            }
        )
    };

    export let todo: todoI;
</script>

<main>
    <div class="todo-item">
        <p>
            <input
                    type='checkbox'
                    checked={todo.completed}
                    on:change={markComplete(todo.id)}
            />{' '}
            <span completed={todo.completed ? "true" : "false"}>{todo.title}</span>
            <button on:click={delTodo(todo.id)} class="btn">
                x
            </button>
        </p>
    </div>
</main>

<style lang="scss">
  .todo-item {
    background: #f4f4f4;
    padding: 20px 20px;
    margin: 2rem 10% 0;
    border-bottom: 1px #ccc dotted;
    border-radius: 15px;
  }

  .btn {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 13px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }

  [completed=true] {
    text-decoration: line-through;
  }
</style>