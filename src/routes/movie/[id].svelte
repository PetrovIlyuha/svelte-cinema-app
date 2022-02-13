<script context="module">
	const BASE_URL = 'https://api.themoviedb.org/3';
	export async function load({ fetch, params }) {
		const res = await fetch(
			`${BASE_URL}/movie/${params.id}?api_key=${import.meta.env.VITE_API_KEY}&language=en-US`
		);
		const data = await res.json();
		console.log(data);
		if (res.ok) {
			return {
				props: { movieDetails: data }
			};
		}
	}
</script>

<script>
	import { fly } from 'svelte/transition';
	export let movieDetails;
</script>

<div
	class="movie_details"
	in:fly={{ y: 30, duration: 500, delay: 500 }}
	out:fly={{ y: 30, duration: 500 }}
>
	<div class="img_container">
		<img src={`https://image.tmdb.org/t/p/original/${movieDetails.backdrop_path}`} alt="" />
	</div>
	<div class="text-container">
		<h1 class="title">{movieDetails.title}</h1>
		<p class="overview">{movieDetails.overview}</p>
		<h4><span>Budget:</span> ${movieDetails.budget}</h4>
		<h4><span>Rating:</span> {movieDetails.vote_average}</h4>
		<h4><span>Running Time:</span> {movieDetails.runtime} mins</h4>
	</div>
</div>

<style>
	.img_container {
		width: 100%;
	}
	img {
		border-radius: 1rem;
		width: 100%;
		height: 50vh;
		object-fit: cover;
	}

	.movie_details {
		margin: 4rem 10%;
		display: flex;
		gap: 4rem;
	}
	span {
		font-weight: 700;
		font-size: 1.3rem;
	}

	.text-container {
		display: flex;
		flex-direction: column;
		justify-content: space-around;
	}

	.overview {
		font-size: 1.3rem;
	}

	@media screen and (max-width: 1150px) {
		.movie_details {
			flex-direction: column;
		}
	}
</style>
