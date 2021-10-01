<script>
	import Header from "./Header.svelte"
	import Chat from "./Chat.svelte";
</script>

<main class="min-h-screen bg-gray-50">
	<Header />
	<Chat />
</main>

<style global lang="postcss">
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>
