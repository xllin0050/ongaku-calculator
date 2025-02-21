<script lang="ts">
  export let currentTempo: number;
  export let tempoChanged: (value: number) => void;
  import { Plus, Minus } from 'lucide-svelte';
  
  function handleInput(event: Event) {
    const input = event.target as HTMLInputElement;
    const value = parseInt(input.value);
    if (!isNaN(value) && value > 0) {
      tempoChanged(value);
    }
  }

  function increaseTempo() {
    tempoChanged(currentTempo + 1);
  }

  function decreaseTempo() {
    if (currentTempo > 1) {
      tempoChanged(currentTempo - 1);
    }
  }
</script>

<div class="tempo-input">
  <button on:click={decreaseTempo} aria-label="Decrease Tempo">
    <Minus />
  </button>
  <input 
    type="number" 
    min="1"
    bind:value={currentTempo}
    on:input={handleInput}
  />
  <button on:click={increaseTempo} aria-label="Increase Tempo">
    <Plus />
  </button>
</div>

<style>
  .tempo-input {
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .tempo-input input {
    font-size: 1.2rem;
    padding: 0.5rem;
    width: 100px;
    text-align: center;
  }

  .tempo-input button {
    background: none;
    border: none;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0.5rem;
  }
</style>
