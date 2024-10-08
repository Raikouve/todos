<script>
	import { onMount } from "svelte";

  let todos = [];
  let todoText = "";

  onMount(() => {
    const existingTodos = localStorage.getItem('todos');
    todos = JSON.parse(existingTodos || []);
  });

  function addTodo() {
    todos = [...todos, todoText];
    localStorage.setItem('todos', JSON.stringify(todos));
  }
</script>


<div>
  <div>
    <input type="text" placeholder="Tarefa" bind:value={todoText} />
    <button id="btn-add-todo" on:click={addTodo}>+</button>
  </div>
  <ul id="todo-list">
    {#each todos as todo}
      <li>{todo}</li>
    {/each}
  </ul>
</div>