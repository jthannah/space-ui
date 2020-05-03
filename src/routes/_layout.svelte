<script context="module">
	export async function preload(page, session) {

		const response = await this.fetch(`http://localhost:3001/image-of-the-day`);
		const dailyImage = await response.json();

		return { dailyImage };
	}
</script>

<script>
	import Nav from '../components/Nav.svelte';
	import Hamburger from "../components/Hamburger.svelte";
	import Overlay from "../components/Overlay.svelte"
	import { setContext } from 'svelte'

	export let segment;
	export let dailyImage;

	setContext('dailyImage', dailyImage);

	let menuActive = false
</script>

<svelte:head>
	<title>All About Space</title>
	{@html `<style> body { background: url("${dailyImage.url}") center center no-repeat; background-size: cover;}</style>`}
</svelte:head>

<Nav {segment} bind:menuActive/>
<Overlay bind:menuActive />
<Hamburger bind:menuActive />
<main>
	<slot></slot>
</main>

<style>
	main {
		color: #fcfbfe;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
		transition: all .25s ease-out;
		min-height: 100vh;
    color: white;
    flex: 1 1 100%;
		margin-left: calc(30px + 2rem);
	}
</style>