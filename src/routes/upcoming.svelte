<script context="module">
	const BASE_URL = 'https://api.themoviedb.org/3';
	export async function load({ fetch }) {
		const response = await fetch(
			`${BASE_URL}/movie/upcoming?api_key=${import.meta.env.VITE_API_KEY}&language=en-US&page=1`
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
	import MoviesGrid from '../components/MoviesGrid.svelte';
	export let movies;
</script>

<section in:fly={{ y: 30, duration: 500, delay: 500 }} out:fly={{ y: 30, duration: 500 }}>
	<MoviesGrid {movies} heading="Upcoming Movies" />
</section>
