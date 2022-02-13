<script context="module">
	const BASE_URL = 'https://api.themoviedb.org/3';
	export async function load({ fetch }) {
		const response = await fetch(
			`${BASE_URL}/movie/popular?api_key=${import.meta.env.VITE_API_KEY}`
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
	import MovieGrid from '../components/MoviesGrid.svelte';
	export let movies;
	import { fly } from 'svelte/transition';
</script>

<section in:fly={{ y: 30, duration: 500, delay: 500 }} out:fly={{ y: 30, duration: 500 }}>
	<MovieGrid {movies} heading="Popular Movies" />
</section>
