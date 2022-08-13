<script>
  import { labels } from '../common/constants.js';

  export let toDo = {
    id: 0,
    title: labels.defaultTitle,
    content: labels.defaultContent,
  };
  export let handleDeleteToDO = () => {};
  export let handleOpenEditModal = () => {};
</script>

<div
  class="item-container"
  on:click={() => handleOpenEditModal(toDo)}
>
  <div class="item">
    <img
      src="/removeIcon.png"
      alt=""
      class="remove"
      on:click={handleDeleteToDO(toDo.id)}
    />
    <div class="title">
      {toDo.title}
    </div>
    <div class="content">
      {toDo.content}
    </div>
  </div>
</div>

<style lang="scss">
  .item-container {
    width: 100%;
    max-width: 400px;
    min-width: 270px;
    cursor: pointer;
    .item {
      width: calc(100% - 2rem);
      padding: 1rem;
      font-size: 1.3rem;
      display: flex;
      align-items: flex-start;
      justify-content: flex-start;
      flex-direction: column;
      border-radius: 8px;
      box-shadow: 0px 0px 12px 4px rgba(59,59,59,0.1);
      background-color: #FFFFFF;
      color: #2a2a2a;
      .remove {
        width: 24px;
        border-radius: 50%;
        cursor: pointer;
        margin: 0 0 0 auto;
        display: flex;
        justify-content: center;
        align-items: center;
      }
      .title {
        font-weight: 600;
        width: 100%;
        padding: 0.2rem 0 0.7rem;
      }
      .container {
        width: 100%;
      }
    }
  }
</style>