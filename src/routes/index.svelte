<script context="module">
	export async function load() {
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/popular?api_key=5757894f6212d16cce254b92ecf73187&language=en-US&page=1`
		);

		const data = await res.json();
		if (res.ok) {
			return { props: { popular: data.results } };
		}
	}
</script>

<script>
	import PopularMovies from '../components/PopularMovies.svelte';
	import Search from '../components/Search.svelte';
	import { fly } from 'svelte/transition';
	import global from '../global.css';
	export let popular;
</script>

<section in:fly={{ x: 50, duration: 500, delay: 500 }} out:fly={{ y: 50, duration: 500 }}>
	<Search />
	<PopularMovies popMovies={popular} />
</section>
