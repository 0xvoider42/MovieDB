<script context="module">
	export async function load({ params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/search/movie?api_key=5757894f6212d16cce254b92ecf73187&language=en-US&query=${params.id}&page=1&include_adult=true`
		);

		const data = await res.json();
		if (res.ok) {
			return { props: { searchMovie: data.results } };
		}
	}
</script>

<script>
	import Cards from '../../components/Cards.svelte';
	export let searchMovie;
</script>

<div class="search-movies">
	{#each searchMovie as movie}
		<Cards {movie} />
	{/each}
</div>

<style>
	.search-movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column-gap: 1rem;
		grid-row-gap: 2rem;
		height: 20vh;
	}
</style>
