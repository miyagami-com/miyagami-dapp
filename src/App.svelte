<script>
	import Header from "./Header.svelte"
	import Chat from "./Chat.svelte";
	import Banner from "./Banner.svelte";
</script>

<main class="bg-gray-50 h-screen">
	<Header />
	<Banner />
	<Chat />
</main>

<style global lang="postcss">
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>
