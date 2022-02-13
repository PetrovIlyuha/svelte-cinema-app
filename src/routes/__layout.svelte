<script>
	import global from '../global.css';
	import NavBar from '../components/NavBar.svelte';
	import SearchMovies from '../components/SearchMovies.svelte';
</script>

<svelte:head>
	<title>Nema Cinema</title>
</svelte:head>

<div class="page_layout">
	<NavBar />
	<div class="search">
		<SearchMovies />
	</div>
</div>
<slot />

<style>
	.page_layout {
		width: 80vw;
		margin: 0 auto;
	}
	.search {
		padding: 1rem;
	}
</style>
