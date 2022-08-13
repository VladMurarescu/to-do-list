<script>
  import Item from './Item.svelte';

  export let toDoList = [];
  export let handleDeleteToDO = () => {};
  export let handleOpenEditModal = () => {};
</script>

<div class="list-container">
  {#each toDoList as toDo (`${toDo.content}_${Math.random() * 1000}`)}
    <Item
      toDo={toDo}
      handleDeleteToDO={handleDeleteToDO}
      handleOpenEditModal={handleOpenEditModal}
    />
  {/each}
</div>

<style lang="scss">
  .list-container {
    width: calc(100% - 4rem);
    padding: 2rem;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: flex-start;
    gap: 1.5rem;
    margin: auto;
    flex-wrap: wrap;
    &:empty {
      display: none;
    }
  }
</style>
