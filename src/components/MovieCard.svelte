<script>
	export let movie;
</script>

<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
	<link
		href="https://fonts.googleapis.com/css2?family=Exo+2:wght@300;400;500;700&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<div class="movie-card">
	<a href={`/movie/${movie.id}`}>
		<div class="img_container">
			<img src={`https://image.tmdb.org/t/p/w500/${movie.poster_path}`} alt="movie poster" />
		</div>
	</a>
	<div class="description">
		<h2 class="title">
			{movie.title.length > 30 ? movie.title.substring(0, 31) + '...' : movie.title}
		</h2>
		<p class="released">{movie.release_date}</p>
	</div>
</div>

<style>
	.movie-card {
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		min-height: 40vh;
		margin-bottom: 1rem;
	}
	.img_container {
		overflow: hidden;
		border-radius: 1rem;
	}
	img {
		width: 100%;
		height: 400px;
		object-fit: cover;
		border-radius: 1rem;
		transition: all 0.2s ease-in;
		filter: grayscale(0.5);
	}
	img:hover {
		transform: scale(1.1);
		filter: none;
	}
	.description {
		height: 5rem;
	}
	.title {
		font-weight: 700;
		font-size: 1.2rem;
	}
	.released {
		font-weight: 500;
		font-size: 0.8rem;
	}
</style>
