<script lang="ts">
  export let scaleType: string;
  export let scaleTypeChanged: (value: string) => void;
  
  const scaleTypes = [
    "major",
    "minor",
    "harmonic minor",
    "melodic minor",
    "pentatonic"
  ];
</script>

<div class="scale-select">
  {#each scaleTypes as type}
    <button
      class:active={scaleType === type}
      on:click={() => scaleTypeChanged(type)}
    >
      {type}
    </button>
  {/each}
</div>

<style>
  .scale-select {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
    justify-content: center;
  }
  
  button {
    padding: 0.5rem 1rem;
    border: 1px solid #ddd;
    border-radius: 4px;
    background: white;
    cursor: pointer;
    text-transform: capitalize;
  }
  
  button.active {
    background: #333;
    color: white;
  }
</style>
