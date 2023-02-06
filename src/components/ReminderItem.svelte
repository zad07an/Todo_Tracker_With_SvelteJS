<script>
  import { reminderData } from "../stores/stores";
  import {fade, scale} from 'svelte/transition'

  export let todo;

  const deleteItem = (itemId) => {
    reminderData.update((data) => {
      return data.filter((item) => item.id !== itemId.id);
    })
  }
</script>

<div class="display_item" in:scale out:fade>
  <div>
    <input type="checkbox" bind:checked={todo.isCompleted} id={`${todo.id}${todo.title}`}>
    <label for={`${todo.id}${todo.title}`}>{todo.title}</label>
  </div>
  <button on:click={deleteItem(todo)}>X</button>
</div>

<style scoped>
  .display_item {
    width: 100%;
    min-height: 60px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
    border-bottom: 1px solid #ccc;
  }

  .display_item:nth-last-child(1) {
    border: none;
  }

  .display_item > div {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    gap: 10px;
  }

  .display_item > div > input {
    width: 16px;
    height: 16px;
    accent-color: green;
  }

  .display_item > div > label {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    font-size: 20px;
  }

  .display_item > button {
    width: 60px;
    height: 30px;
    border: none;
    background: crimson;
    color: white;
    font-size: 18px;
    font-weight: bold;
    cursor: pointer;
  }
</style>