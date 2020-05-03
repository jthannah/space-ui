<script>
	import {getContext} from 'svelte';
	import { format, parseISO } from 'date-fns'

	let dailyImage = getContext('dailyImage');

	let todaysDate =  format(new Date(), 'y-MM-dd');
	let selectedDate = todaysDate;

	$: formattedDate = format(parseISO(selectedDate), 'MMMM d, y')

	// Make api call to get new image....

</script>

<svelte:head>
	<title>All About Space: Photo of the day</title>
</svelte:head>

<div id="content">
	<p>{selectedDate}</p>
	<h1>Photo of the day on {formattedDate}</h1>
	<p>Choose a day to see the photo of the day for that date:
		<input type="date" bind:value="{selectedDate}" max="{todaysDate}" >
	</p>

	<div class="image-result">
		<h2>{dailyImage.title}</h2>
		<p>
			<img src="{dailyImage.url}" alt="{dailyImage.title}" title="{dailyImage.title}"/>
			{dailyImage.explanation}
		</p>
	</div>
</div>

<style lang="stylus">
	#content {
		background: rgba(0,0,0,0.8);
		backdrop-filter: blur(6px);
		border-radius: 5px;
		width: 75%;
		margin: 0 auto;
		padding: 1rem 2rem;
	}

	input {
		padding: 0.5rem 1rem;
		font-size: 1rem;
		cursor: pointer;
		border: 0;
		border-radius: 3px;
	}

	img {
		float: left;
		padding: 0 1rem 1rem 0;
		max-width: 50%;
	}
</style>