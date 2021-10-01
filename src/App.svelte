<script>
	import Header from "./Header.svelte"
	import Login from "./Login.svelte"
	import Chat from "./Chat.svelte"
	import { username } from './user'
	export let name;


</script>

<main>
	
	<Header />
	{#if !$username}
		<Login />
	{:else}
		<Chat/>
	{/if}
</main>

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