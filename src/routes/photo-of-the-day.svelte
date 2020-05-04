<script>
	import { fade } from 'svelte/transition';
	import Loader from '../components/Loader.svelte';
	import {getContext} from 'svelte';
	import { format, parseISO } from 'date-fns'

	let todaysDate =  format(new Date(), 'y-MM-dd');
	let selectedDate = todaysDate;

	async function getPhotoOfTheDay() {
		let data = "";
		if (selectedDate !== todaysDate) {
			let response = await fetch(`http://localhost:3001/image-of-the-day/` + selectedDate);
			data = await response.json();
		} else {
			console.log("use in memory data");
			data = getContext('dailyImage');
		}
		return data;
	}

	$: imageData = getPhotoOfTheDay(selectedDate);
	$: formattedDate = format(parseISO(selectedDate), 'MMMM d, y')
</script>

<svelte:head>
	<title>All About Space: Photo of the day</title>
</svelte:head>

<div id="content">
	<h1>Photo of the day on {formattedDate}</h1>
	<p class="instructions">Choose a day to see the photo of the day for that date:
		<input type="date" bind:value="{selectedDate}" max="{todaysDate}" >
	</p>

	{#if imageData===""}

		<p>error.. no data for the selected date</p>

	{:else}

		{#await imageData}
			<Loader show="true"/>
		{:then imageData}
			<div class="image-result" transition:fade="{{duration: 300}}">
				<h2>{imageData.title}</h2>
				<p>
					<img src="{imageData.url}" alt="{imageData.title}" title="{imageData.title}"/>
					{imageData.explanation}
				</p>
			</div>
		{:catch error}

		{error.message}

		{/await}

	{/if}
</div>

<style lang="stylus">
	#content {
		background: rgba(0,0,0,0.8);
		backdrop-filter: blur(6px);
		border-radius: 5px;
		width: 75%;
		margin: 0 auto;
		padding: 1rem 2rem;

		&:after {
			clear: both;
			content: "";
			display: block;
			width: 100%;
		}
	}

	.instructions {
		border-bottom: 1px solid gray;
		padding-bottom: 2rem;
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