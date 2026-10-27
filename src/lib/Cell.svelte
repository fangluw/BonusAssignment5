<script>
  let { on = false, onToggle } = $props();
</script>

<button
  class="cell"
  class:on={on}
  onclick={onToggle}
  aria-label="Toggle cell"
></button>

<style>
  .cell {
    width: 100px;
    height: 100px;
    border: 1px solid grey;
    background-color: white;
    padding: 0;
    display: block;
    box-sizing: border-box;
  }

  .cell.on {
    background-color: black;
  }
</style>