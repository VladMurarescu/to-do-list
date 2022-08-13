<script>
  export let isInputVisible = false;
</script>

<img
  src="/addIcon.png"
  on:click={() => {
    if (!isInputVisible) isInputVisible = true;
  }}
  alt=""
/>

<style lang="scss">
  img {
    width: 48px;
    height: 48px;
    cursor: pointer;
    margin: auto;
    display: flex;
    transition: all 0.5s ease;
    &:hover {
      transform: scale(1.2);
    }
  }
</style>