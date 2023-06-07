<script lang="ts">
	import { tick, onMount } from 'svelte';

	let loaded: boolean = false;
	let flipped: boolean = false;

	export const random = async () => {
		flipped = Math.random() < 0.5;
		await tick();
		if (randomise) setTimeout(random, 20);
	};

	onMount(() => {
		loaded = true;
	});

	$: allBlack && (flipped = true);
	$: allOn && (flipped = false);

	$: loaded && randomise && random();

	export let x: number;
	export let y: number;
	export let color: string = '';
	export let allBlack: boolean;
	export let allOn: boolean;
	export let randomise: boolean;
	export let disk: HTMLElement;
</script>

<div
	class={flipped ? 'disk-frame disk-frame-flip' : 'disk-frame'}
	bind:this={disk}
	style="--dot-colour: {color}"
>
	<div class="diskFrame_tl" />
	<div class="diskFrame_bl" />
	<div class="diskFrame_tr" />
	<div class="flip">
		<div class="disk-front" />
		<div class="disk-back" />
		<div class="tag" />
	</div>
</div>

<style>
	.disk-frame {
		position: relative;
		height: 40px;
		width: 40px;
		background-color: transparent;
		perspective: 1000px; /* Remove this if you don't want the 3D effect */
	}
	.flip {
		position: relative;
		width: 100%;
		height: 100%;
		transition: transform 0.1s;
		transform-style: preserve-3d;
	}
	.diskFrame_tl {
		position: absolute;
		top: 2px;
		left: 2px;
		background: black;
		width: 4px;
		height: 4px;
	}
	.diskFrame_bl {
		position: absolute;
		bottom: 2px;
		left: 2px;
		background: black;
		width: 4px;
		height: 4px;
	}
	.diskFrame_tr {
		position: absolute;
		right: 2px;
		top: 2px;
		background: black;
		width: 4px;
		height: 4px;
	}
	.disk-front {
		display: flex;
		position: relative;
		background: var(--dot-colour);
		filter: drop-shadow(2px 2px 2px black);
		border-radius: 20mm;
		height: 40px;
		width: 40px;
		overflow: visible;
	}
	.disk-back {
		display: flex;
		position: absolute;
		background: #1e1e1e;
		filter: drop-shadow(2px 2px 2px black);
		border-radius: 20mm;
		height: 40px;
		width: 40px;
		overflow: visible;
		transform: rotateY(180deg);
	}
	/* Position the front and back side */
	.disk-front,
	.disk-back {
		position: absolute;
		width: 100%;
		height: 100%;
		-webkit-backface-visibility: hidden; /* Safari */
		backface-visibility: hidden;
	}
	.disk-frame-flip .flip {
		transform: rotateY(180deg);
	}
	.tag {
		position: absolute;
		font-size: 0.6rem;
		background: #2a2a2a;
		bottom: 3px;
		right: 3px;
		width: 6px;
		height: 6px;
		border-radius: 3px;
	}
</style>
