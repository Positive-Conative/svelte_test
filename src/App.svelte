<script>
	import Hello from './hello.svelte';	//자식

	import {myStore} from './store.js';
	console.log(myStore);
	console.log($myStore);	//데이터 자동 구독  asdf
	let asdf = "hellooo";

	$myStore = asdf;
	// export let name;
</script>

<main>
	a
	<!-- <h1>Hello {name}!</h1> -->
	<!-- <p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p> -->
</main>

<!-- props -->
<Hello /> 


<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>