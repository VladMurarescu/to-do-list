<script>
  import AddInput from './AddInput.svelte';
  import CreateToDo from './CreateToDo.svelte';
  import List from './List.svelte';
  import EditModal from './EditModal.svelte';

  let textAreaValue = '';
  let inputValue = ''
  let toDoList = [];
  let isInputVisible = false;
  let isEditModalVisible = false;
  let currentToDo = null;
  const handleOpenEditModal = (item) => {
    currentToDo = item;
    isEditModalVisible = true;
  };

  const handleAddToDo = () => {
    if (!inputValue || !textAreaValue) return;
    const newToDo = {
      id: Math.random() * 1000,
      title: inputValue,
      content: textAreaValue,
    }
    toDoList = [...toDoList, newToDo];
    inputValue = '';
    textAreaValue = '';
    isInputVisible = false;
    isEditModalVisible = false;
  }
  const handleDeleteToDO = (id) => {
    toDoList = toDoList.filter((item) => item.id !== id);
  }
</script>

<CreateToDo
  bind:isInputVisible
/>
{#if isInputVisible}
  <AddInput
    bind:inputValue
    bind:textAreaValue
    handleAddToDo={handleAddToDo}
  />
{/if}
{#if toDoList.length}
  <List
    toDoList={toDoList}
    handleDeleteToDO={handleDeleteToDO}
    handleOpenEditModal={handleOpenEditModal}
  />
{/if}
{#if isEditModalVisible}
  <EditModal
    toDo={currentToDo}
    bind:toDoList
    bind:isEditModalVisible
  />
{/if}