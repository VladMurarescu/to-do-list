<script>
  import { slide } from 'svelte/transition';
  import { labels } from '../common/constants.js';

  export let inputValue = '';
  export let textAreaValue = '';
  export let isEditModalOpen = false;
  export let handleEditNote = () => {};
  export let handleAddToDo = () => {};
</script>

<div
  class="container"
  transition:slide|local={{duration: 700}}
>
  <input
    bind:value={inputValue}
    type="text"
    placeholder={labels.inputPlaceholder}
  />
  <textarea
    bind:value={textAreaValue}
    placeholder={labels.textAreaPlaceholder}
  ></textarea>
  <div class="buttons">
    <div
      class="button"
      class:disabled={!inputValue || !textAreaValue}
      on:click={() => {
        if (isEditModalOpen) {
          handleEditNote()
        } else {
          handleAddToDo()
        }
      }}
    >
      {isEditModalOpen ? labels.edit : labels.add}
    </div>
  </div>
</div>

<style lang="scss">
  .container {
    width: calc(100% - 2rem);
    padding: 2rem 1rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    max-width: 500px;
    margin: 0 auto;
    & > *:not(:last-child) {
      margin: 0 0 1rem 0;
    }
    input {
      width: calc(100% - 20px);
      height: 20px;
      margin: 0 0 1rem 0;
      border-radius: 8px;
      padding: 10px;
      resize: none;
      font-size: 1.2rem;
      outline: none;
      border: none;
      box-shadow: 0px 0px 12px 4px rgba(59,59,59,0.1);
      color: #2a2a2a;
      &:focus,
      &:active {
        outline: none;
        border: none;
      }
    }
    textarea {
      width: calc(100% - 20px);
      height: 150px;
      border-radius: 8px;
      padding: 10px;
      resize: none;
      font-size: 1.2rem;
      outline: none;
      border: none;
      box-shadow: 0px 0px 12px 4px rgba(59,59,59,0.1);
      color: #2a2a2a;
      &:focus,
      &:active {
        outline: none;
        border: none;
      }
    }
    .buttons {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 100%;
      .button {
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 8px;
        padding: 10px 15px;
        cursor: pointer;
        background-color: #FFFFFF;
        font-size: 1.2rem;
        box-shadow: 0px 0px 12px 4px rgba(59,59,59,0.1);
        color: #2a2a2a;
      }
      .disabled {
        opacity: 0.6;
        cursor: not-allowed;
      }
    }
  }
</style>