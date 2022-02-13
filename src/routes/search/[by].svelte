<script context="module">
	const BASE_URL = 'https://api.themoviedb.org/3';
	export async function load({ fetch, params: { by } }) {
		const response = await fetch(
			`${BASE_URL}/search/movie?api_key=${
				import.meta.env.VITE_API_KEY
			}&query=${by}&language=en-US&page=1&include_adult=false`
		);
		const data = await response.json();
		if (response.ok) {
			return {
				props: { movies: data.results }
			};
		}
	}
</script>

<script>
	import { fly } from 'svelte/transition';
	import MovieGrid from '../../components/MoviesGrid.svelte';
	export let movies;
</script>

<section in:fly={{ y: 30, duration: 500, delay: 500 }} out:fly={{ y: 30, duration: 500 }}>
	<MovieGrid {movies} heading="Movies Found for Your Search." />
</section>
