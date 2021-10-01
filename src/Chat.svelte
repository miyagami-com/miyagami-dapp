
<script>
    import Login from "./Login.svelte";
    import Message from "./Message.svelte";
    import { username, user } from './user'

</script>

<div>
    {#if $username}
        <Message />
    {:else}
        <main>
            <Login />
        </main>
    {/if}
</div>
