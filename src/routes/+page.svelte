<script lang="ts">
	import { onMount } from 'svelte';
	let baubau = 0;
	let baubauNoise: HTMLAudioElement;

	function playBaubau() {
		let audioClone: HTMLAudioElement = baubauNoise.cloneNode(false) as HTMLAudioElement;
		baubau++;

		audioClone.play();

		audioClone.addEventListener('ended', function () {
			this.remove();
		});
	}

	onMount(() => {
		baubauNoise = new Audio('/noises/baubau.mp3');
		baubauNoise.preload = 'auto';

		return baubauNoise.remove;
	});
</script>

<h1>{baubau}</h1>
<button on:click={playBaubau}>Bau!</button>
