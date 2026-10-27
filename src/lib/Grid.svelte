<script>
  import Cell from './Cell.svelte';

  let grid = $state(
    Array.from({length:4}, (_, id) => ({id, on: false}))
  );

  let onCount = $derived(grid.filter((cell) => cell.on).length);

  function toggleCell(index) {
    grid[index].on = !grid[index].on;
  }
</script>

<div class="container">
    <h1>Count: {onCount}</h1>

  <div class="grid">
    {#each grid as cell, i (cell.id)}
      <Cell on={cell.on} onToggle={() => toggleCell(i)}
      />
    {/each}
  </div>
</div>

<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .container h1 {
    margin: 0;
    font-size: 1.5rem;
    font-weight: 600;
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(2, 100px);
    grid-template-rows: repeat(2, 100px);
    gap: 0;
  }
</style>