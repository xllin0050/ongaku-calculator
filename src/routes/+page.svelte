<script lang="ts">
	import BeatsTable from '$lib/components/BeatsTable.svelte';
	import NoteTable from '$lib/components/NoteTable.svelte';
	import PitchNameInput from '$lib/components/PitchNameInput.svelte';
	import ScaleTypeSelect from '$lib/components/ScaleTypeSelect.svelte';
	import TempoInput from '$lib/components/TempoInput.svelte';
	import { onMount } from 'svelte';

	let tempo = 120;
	let qNoteLengthMs = 0;
	let pitchName = 'C';
	let scaleType = 'major';

	$: {
		const minute = 60 * 1000;
		qNoteLengthMs = minute / tempo;
	}
</script>

<main>
	<div class="description">beats per minute:</div>

	<div class="center">
		<TempoInput currentTempo={tempo} tempoChanged={(v) => (tempo = v)} />
	</div>

	<BeatsTable {qNoteLengthMs} />

	<div class="description">select your scale</div>
	<ScaleTypeSelect {scaleType} scaleTypeChanged={(v) => (scaleType = v)} />

	<div class="description">select your pitch name</div>
	<PitchNameInput pitchNameChanged={(v) => (pitchName = v)} />

	<NoteTable {pitchName} {scaleType} />
</main>

<style>
	main {
		padding: 2rem;
		max-width: 800px;
		margin: 0 auto;
	}

	.description {
		text-transform: capitalize;
		text-align: center;
		margin: 2rem 0 1rem;
		font-size: 1.2rem;
		color: #666;
	}

	.center {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 1rem;
	}
</style>
