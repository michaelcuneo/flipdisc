<script>
	import Fa from 'svelte-fa';
	import { faCog } from '@fortawesome/free-solid-svg-icons';
</script>

<header>
	<h2>AlfaZeta XY5 Flipdot Emulator</h2>
</header>

<div class="fa">
	<Fa icon={faCog} size="2x" />
</div>

<style>
	header {
		position: absolute;
		top: 0;
	}
	.fa {
		position: absolute;
		top: 15px;
		right: 15px;
		color: #2e2e2e;
		transition: transform 0.2s;
	}
	.fa:hover {
		transform: scale(1.1);
		transition: transform 0.2s;
	}
	h2 {
		color: var(--color-text);
	}
</style>
