<script>
	import {getContext} from 'svelte';
	const dailyImage = getContext('dailyImage');
</script>

<div>
	<h1>{dailyImage.title}</h1>
	<p>{dailyImage.explanation}</p>
</div>

<style lang="stylus">
	div {
		color: #fcfbfe;
		text-shadow: 1px 1px black;
	}

	p {
		font-size: 1.5rem;
	}
</style>