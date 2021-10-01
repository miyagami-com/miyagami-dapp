<script>
	import Header from "./Header.svelte"
	import Login from "./Login.svelte"
	import Message from "./Message.svelte";

	export let name;
</script>

<main>
	<Header />
	<Login />
</main>

<style global lang="postcss">
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>
