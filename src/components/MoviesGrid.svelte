<script>
	export let movies, heading;
	import MovieCard from './MovieCard.svelte';
	// import global from '../global.css';
</script>

<div class="page_layout">
	<h3>{heading}</h3>
	<div class="movies">
		{#each movies as movie}
			<MovieCard {movie} />
		{/each}
	</div>
</div>

<style>
	.page_layout {
		width: 80vw;
		margin: 0 auto;
	}
	h3 {
		font-size: 2rem;
	}
	.movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-gap: 2rem;
	}
</style>
