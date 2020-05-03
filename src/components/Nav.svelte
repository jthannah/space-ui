<script>
	export let segment;
	export let menuActive = false;
</script>

<nav class:active="{menuActive}">
	<ul class="menu-items">
		<li class="menu-item"><a aria-current='{segment === undefined ? "page" : undefined}' href='.'>Home</a></li>
		<li class="menu-item"><a aria-current='{segment === "photo-of-the-day" ? "page" : undefined}' href='photo-of-the-day'>Photo of the Day</a></li>
		<li class="menu-item"><a aria-current='{segment === "earth" ? "page" : undefined}' href='earth'>Earth</a></li>
		<li class="menu-item"><a aria-current='{segment === "near-objects" ? "page" : undefined}' href='near-objects'>Near Objects</a></li>
		<li class="menu-item"><a aria-current='{segment === "natural-events" ? "page" : undefined}' href='natural-events'>Natural Events</a></li>

		<li class="menu-item"><a aria-current='{segment === "mars" ? "page" : undefined}' href='mars'>Mars</a></li>
		<li class="menu-item"><a aria-current='{segment === "mars-rover" ? "page" : undefined}' href='mars-rover'>Mars Rover</a></li>
		<li class="menu-item"><a aria-current='{segment === "mars-weather" ? "page" : undefined}' href='mars-weather'>Mars Weather</a></li>

		<!-- for the blog link, we're using rel=prefetch so that Sapper prefetches
		     the blog data when we hover over the link or tap it on a touchscreen -->
		<li class="menu-item"><a rel=prefetch aria-current='{segment === "media-library" ? "page" : undefined}' href='media-library'>Media Library</a></li>
	</ul>
</nav>


<style lang="stylus">
	nav {
		width: 25%;
		transform: translateX(calc(100% * -1));
		background: linear-gradient(to bottom right, rgba(186, 30, 104, 0.9), rgba(86, 67, 253, 0.9));
		display: flex;
		justify-content: center;
		align-items: center;
		position: fixed;
		top: 0;
		height: 100vh;
		transition: all .25s ease-out;
		z-index: 2;
	}

	.active {
		transform: translateX(0);
	}

	.menu-items
		list-style none
		padding 0

		.menu-item
			color #fcfbfe
			font-size 1.25rem
			padding 0.5rem
			transition color .3s

			&:hover
				color #7649fe

</style>