<script>
  import {v4 as uuidv4} from 'uuid';
  import { reminderData } from "../stores/stores";


  let text = '';
  let message = ''
  let messageIs = false

  const handleSubmit = () => {
    if (text.trim().length <= 10) {
      message = 'Text must be at least 10 characters!'
      messageIs = true
    } else if (text.trim().length !== 0) {
      const newTodo = {
        id: uuidv4(),
        title: text,
        isCompleted: false
      }
      reminderData.update((data) => {
        return [newTodo, ...data]
      })
      text = ''
      messageIs = false
    }
  }
</script>

<form action="" class="form" on:submit|preventDefault={handleSubmit}>
  <input type="text" bind:value={text} placeholder="What do you have planned today?">
  <button>Add</button>
</form>
{#if messageIs}
  <div class="warning_message">
    <p>{message}</p>
  </div>
{/if}

<style scoped>
  .form {
    height: 40px;
    display: grid;
    grid-template-columns: 5fr 1fr;
    grid-gap: 5px;
    padding: 0 10px;
  }

  .form > input {
    padding: 10px;
    font-size: 18px;
    border: 1px solid #ccc;
    outline: 0;
  }

  .form > button {
    font-size: 18px;
    text-transform: uppercase;
    font-weight: bold;
    background: black;
    color: white;
    border: none;
    cursor: pointer;
  }

  .warning_message {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .warning_message > p {
    font-size: 16px;
    color: crimson;
  }
</style>