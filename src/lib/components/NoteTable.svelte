<script lang="ts">
  export let pitchName: string;
  export let scaleType: string;
  
  $: notes = calculateScale(pitchName, scaleType);
  
  function calculateScale(pitch: string, type: string): string[] {
    const allNotes = ['C', 'C#', 'D', 'D#', 'E', 'F', 'F#', 'G', 'G#', 'A', 'A#', 'B'];
    const intervals = {
      major: [0, 2, 4, 5, 7, 9, 11],
      minor: [0, 2, 3, 5, 7, 8, 10],
      'harmonic minor': [0, 2, 3, 5, 7, 8, 11],
      'melodic minor': [0, 2, 3, 5, 7, 9, 11],
      pentatonic: [0, 2, 4, 7, 9]
    };
    
    const startIndex = allNotes.indexOf(pitch);
    return intervals[type as keyof typeof intervals].map(interval => {
      const noteIndex = (startIndex + interval) % 12;
      return allNotes[noteIndex];
    });
  }
</script>

<div class="note-table">
  <h3>{pitchName} {scaleType} scale</h3>
  <div class="notes">
    {#each notes as note}
      <div class="note">{note}</div>
    {/each}
  </div>
</div>

<style>
  .note-table {
    margin: 1rem 0;
    text-align: center;
  }
  
  .notes {
    display: flex;
    gap: 1rem;
    justify-content: center;
    margin-top: 1rem;
  }
  
  .note {
    padding: 1rem;
    border: 1px solid #ddd;
    border-radius: 50%;
    width: 2.5rem;
    height: 2.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
  }
  
  h3 {
    text-transform: capitalize;
  }
</style>
