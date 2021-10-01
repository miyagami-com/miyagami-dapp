<script>
    import { username,user } from './user'
    import GUN from 'gun';
    import 'gun/sea';
    import 'gun/axe';
    import { onMount } from 'svelte';

    import Login from "./Login.svelte";

    let message = '';
    let messages = []
    const db = GUN();

    // Define db
    onMount(() => {
        db.get('chatmiyagami').map().once( async (v) => {
            messages = [...messages.slice(-100), v]
        });

    })

    // function to create/send message
    function submitMessage() {
        const itemname = new Date().toISOString();
        db.get('chatmiyagami').get(itemname).put({
            text: message,
            user: $username,
            time: new Date().toISOString()
        })
    }

        // encrypt messages

    // function to get more messages

</script>

<div>
    {#if $username}
        {#each messages as message}
            <p> User: {message.user}</p>
            <p> {message.text}</p>
            <p> {message.time}</p>
        {/each}
        <div class="fixed absolute bottom-0">
            <form on:submit|preventDefault={submitMessage}>
                <input bind:value={message}/>
                <button type="submit">say</button>
            </form>
        </div>
    {:else}
        <Login />
    {/if}
</div>
