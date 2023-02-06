<script>
  import {reminderData} from '../stores/stores'
  let todos = [];
  reminderData.subscribe((data) => todos = data);

  const clearAll = () => {
    reminderData.update((data) => {
      return data = [];
    })
  }

  const deleteCompleted = () => {
    reminderData.update((data) => {
      return data.filter((item) => !item.isCompleted);
    })
  }

  $: todosLength = todos.length
</script>

<div class="reminder_footer">
  <div class="todos_length">
    <p>Todos: {todosLength}</p>
  </div>
  <div class="delete_items">
    <button class="clear_completed" on:click={deleteCompleted}>Clear Completed</button>
    <button class="clear_all" on:click={clearAll}>Clear All</button>
  </div>
</div>
<div class="created_with">
  <p>Created with SvelteJS</p>
</div>

<style scoped>
  .reminder_footer {
    height: 50px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 10px;
  }

  .todos_length > p {
    font-size: 20px;
  }

  .delete_items {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
  }

  .clear_all {
    min-width: 120px;
    height: 30px;
    border: none;
    background: crimson;
    color: white;
    font-size: 16px;
    text-transform: uppercase;
    cursor: pointer;
  }

  .clear_completed {
    height: 30px;
    padding: 0 10px;
    border: none;
    background: crimson;
    color: white;
    font-size: 16px;
    text-transform: uppercase;
    cursor: pointer;
  }

  .created_with {
    height: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-top: 1px solid #ccc;
  }

  .created_with > p {
    font-size: 16px;
  }
</style>