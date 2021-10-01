<script>
	import Header from "./Header.svelte"
	import Chat from "./Chat.svelte";
	import Banner from "./Banner.svelte";
	export let name;
</script>

<main class="min-h-screen bg-gray-50 relative overflow-x-hidden">
	<Header />
	<Banner />
	<Chat />
</main>

<style global lang="postcss">
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>
