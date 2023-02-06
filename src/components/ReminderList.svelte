<script>
  import {reminderData} from '../stores/stores'
  import ReminderItem from './ReminderItem.svelte';

  let todos = [];
  reminderData.subscribe((currentData) => todos = currentData);
</script>

<div class="display_list">
  {#if todos.length > 0}
    {#each todos as todo (todo.id)}
    <ReminderItem todo={todo}/>
    {/each}
    {:else}
    <div class="empty_list">
      <p>No todos yet...</p>
    </div>
  {/if}
</div>

<style scoped>
  .display_list {
    height: 240px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-direction: column;
    background: white;
    overflow-y: auto;
  }

  .empty_list {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .empty_list > p {
    font-size: 22px;
  }
</style>