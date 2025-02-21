<script lang="ts">
  export let pitchNameChanged: (value: string) => void;
  
  const pitchNames = ['C', 'C#', 'D', 'D#', 'E', 'F', 'F#', 'G', 'G#', 'A', 'A#', 'B'];
</script>

<div class="pitch-input">
  {#each pitchNames as pitch}
    <button
      on:click={() => pitchNameChanged(pitch)}
    >
      {pitch}
    </button>
  {/each}
</div>

<style>
  .pitch-input {
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
    min-width: 3rem;
  }
  
  button:hover {
    background: #f5f5f5;
  }
</style>
