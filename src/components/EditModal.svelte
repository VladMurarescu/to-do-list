<script>
  import { labels } from '../common/constants.js';
  import { fade } from 'svelte/transition';
  import AddInput from './AddInput.svelte';

  export let toDo = {
    id: 0,
    title: labels.defaultTitle,
    content: labels.defaultContent,
  };
  export let toDoList = [];
  export let isEditModalVisible = false;

  let inputValue = toDo.title;
  let textAreaValue = toDo.content;

  const handleEditNote = () => {
    if (!inputValue || !textAreaValue) return;
    toDoList = toDoList.map((note) => {
      if (note.id === toDo.id) return {
        id: toDo.id,
        title: inputValue,
        content: textAreaValue,
      };
      return note;
    });
    isEditModalVisible = false;
  }
</script>

<div class="modal" transition:fade|local={{duration: 800}}>
 <div class="title-container">
  <div>
    {labels.editNote}
  </div>
  <img
    src="/closeIcon.png"
    alt=""
    on:click={() => isEditModalVisible = false}
  >
 </div>
 <AddInput
  bind:inputValue
  bind:textAreaValue
  handleEditNote={handleEditNote}
  isEditModalOpen
 />
</div>

<style lang="scss">
  .modal {
    z-index: 9999;
    position: fixed;
    width: calc(100% - 2rem);
    height: calc(100vh - 2rem);
    padding: 1rem;
    gap: 2rem;
    top: 0;
    left: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    background-color: rgba(26, 26, 26, 0.8);
   .title-container {
    width: calc(100% - 2rem);
    max-width: 400px;
    padding: 1rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #FFFFFF;
    border-radius: 8px;
    box-shadow: 0px 0px 12px 4px rgba(59,59,59,0.1);
    & > div {
      font-size: 1.3rem;
      font-weight: 600;
    }
    & > img {
      cursor: pointer;
      width: 30px;
    }
   }
  }
</style>