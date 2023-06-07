<script lang="ts">
	import './styles.css';
	import Disk from '$lib/Disk.svelte';

	let color: string;
	let allBlack: boolean = false;
	let allOn: boolean = true;
	let randomise: boolean = false;
	let socket: boolean = false;
	$: color = '#ffdd00';

	let diskArray: any[] = [];
	let rows = 14;
	let columns = 28;

	for (let i: number = 0; i < rows; i++) {
		diskArray[i] = [];
		for (let j: number = 0; j < columns; j++) {
			diskArray[i][j] = j;
		}
	}
</script>

<div class="main">
	{#each diskArray as diskRow, y}
		{#each diskRow as disk, x}
			<Disk {allBlack} {allOn} {color} {randomise} {disk} {x} {y} />
		{/each}
	{/each}
</div>

<div class="colorPicker">
	<input name="colorPicker" bind:value={color} type="color" />
	<button type="button" on:click={() => (allBlack = true)} on:mouseup={() => (allBlack = false)}
		>All Off</button
	>
	<button type="button" on:click={() => (allOn = true)} on:mouseup={() => (allOn = false)}
		>All On</button
	>
	<button type="button" on:click={() => (randomise = !randomise)}>Random Noise</button>
</div>
<p>
	Send Datastream to <a href="http://halide.michaelcuneo.com.au:3000/api/test"
		>http://halide.michaelcuneo.com.au:3000/api/test</a
	>
</p>

<style>
	.main {
		display: flex;
		position: relative;
		flex-wrap: wrap;
		max-width: 1120px;
		background: #2a2a2a;
		padding: 0.2rem;
		box-shadow: 0px 0.5px 0.6px hsl(var(--shadow-color) / 0.38),
			-0.1px 3.3px 3.7px -0.4px hsl(var(--shadow-color) / 0.38),
			-0.2px 6.4px 7.2px -0.8px hsl(var(--shadow-color) / 0.38),
			-0.3px 11.2px 12.6px -1.2px hsl(var(--shadow-color) / 0.38),
			-0.6px 19.1px 21.5px -1.7px hsl(var(--shadow-color) / 0.38),
			-1px 31.5px 35.5px -2.1px hsl(var(--shadow-color) / 0.38),
			-1.5px 49.6px 55.8px -2.5px hsl(var(--shadow-color) / 0.38);
	}
	.colorPicker {
		display: flex;
		flex-direction: row;
		align-items: center;
		padding: 2rem;
	}
	button {
		box-shadow: 0px 0.5px 0.6px hsl(var(--shadow-color) / 0.38),
			-0.1px 1.5px 3.7px -0.4px hsl(var(--shadow-color) / 0.38),
			-0.2px 3.4px 3.2px -0.8px hsl(var(--shadow-color) / 0.38),
			-0.3px 6.2px 6.6px -1.2px hsl(var(--shadow-color) / 0.38),
			-0.6px 9.1px 11.5px -1.7px hsl(var(--shadow-color) / 0.38),
			-1px 15.5px 17.5px -2.1px hsl(var(--shadow-color) / 0.38),
			-1.5px 25.6px 25.8px -2.5px hsl(var(--shadow-color) / 0.38);
		color: #ffffff;
		cursor: pointer;
		display: inline-block;
		font-style: normal;
		overflow: hidden;
		text-align: center;
		text-decoration: none;
		text-overflow: ellipsis;
		transition: all 200ms ease-in-out 0s;
		white-space: nowrap;
		font-weight: 700;
		padding: 6px 14px 5px;
		background-color: #3f8abf;
		font-size: 14px;
		border: none;
	}
	button:hover,
	button:focus,
	button:active {
		background-color: #397cac;
		border-color: #326e99;
	}
	input {
		box-shadow: 0px 0.5px 0.6px hsl(var(--shadow-color) / 0.38),
			-0.1px 1.5px 3.7px -0.4px hsl(var(--shadow-color) / 0.38),
			-0.2px 3.4px 3.2px -0.8px hsl(var(--shadow-color) / 0.38),
			-0.3px 6.2px 6.6px -1.2px hsl(var(--shadow-color) / 0.38),
			-0.6px 9.1px 11.5px -1.7px hsl(var(--shadow-color) / 0.38),
			-1px 15.5px 17.5px -2.1px hsl(var(--shadow-color) / 0.38),
			-1.5px 25.6px 25.8px -2.5px hsl(var(--shadow-color) / 0.38);
		color: #ffffff;
		cursor: pointer;
		display: inline-block;
		font-style: normal;
		overflow: hidden;
		text-align: center;
		text-decoration: none;
		text-overflow: ellipsis;
		transition: all 200ms ease-in-out 0s;
		white-space: nowrap;
		font-weight: 700;
		background-color: #3f8abf;
		border: none;
	}
</style>
