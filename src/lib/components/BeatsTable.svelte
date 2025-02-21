<script lang="ts">
  export let qNoteLengthMs: number;
  
  const beatTypes = [
    { name: "whole", multiplier: 4 },
    { name: "half", multiplier: 2 },
    { name: "quarter", multiplier: 1 },
    { name: "eighth", multiplier: 0.5 },
    { name: "sixteenth", multiplier: 0.25 },
    { name: "thirty-second", multiplier: 0.125 },
    { name: "sixty-fourth", multiplier: 0.0625 }
  ];

  function calculateDotted(ms: number) {
    return ms * 1.5;
  }

  function calculateTriplet(ms: number) {
    return ms * (2 / 3);
  }
</script>

<div class="beats-table">
  <div class="header-row">
    <span>Note Value</span>
    <span>Notes</span>
    <span>Dotted</span>
    <span>Triplets</span>
  </div>
  {#each beatTypes as beat}
    <div class="beat-row">
      <span class="beat-name">{beat.name}</span>
      <span class="beat-value">{(qNoteLengthMs * beat.multiplier).toFixed(2)} ms</span>
      <span class="dotted-value">{calculateDotted(qNoteLengthMs * beat.multiplier).toFixed(2)} ms</span>
      <span class="triplet-value">{calculateTriplet(qNoteLengthMs * beat.multiplier).toFixed(2)} ms</span>
    </div>
  {/each}
</div>

<style>
  .beats-table {
    width: 100%;
    max-width: 600px;
    margin: 1rem auto;
  }
  
  .header-row, .beat-row {
    display: flex;
    justify-content: space-between;
    padding: 0.5rem;
    border-bottom: 1px solid #eee;
  }
  
  .beat-name {
    text-transform: capitalize;
    flex: 1;
  }
  
  .beat-value, .dotted-value, .triplet-value {
    font-family: monospace;
    flex: 1;
    text-align: right;
  }
</style>
