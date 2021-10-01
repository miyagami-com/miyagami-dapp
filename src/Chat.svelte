<script>
    import { username } from './user'
    import GUN from 'gun';
    import 'gun/sea';
    import 'gun/axe';
    import { onMount } from 'svelte';
    import Message from './Message.svelte'

    let newMessage = '';
    import Login from "./Login.svelte";

    let message = '';
    let messages = []
    const db = GUN();
    let key = "thisisthekey"

    // Define db
    onMount(() => {
        console.log(messages)

        db.get('chatMiyagami').map().once( async (data) => {
        var message = {
            text: (await SEA.decrypt(data.text, key)) + '',
            user: data.user,
            time: GUN.state.is(data, 'text')
        }
        messages = [...messages.slice(-100), message]

        });

    })

    // function to create/send message
    async function submitMessage() {

        const secret = await SEA.encrypt(newMessage, key);
        console.log({secret});
        const message = db.get("chatMiyagami").set({
            text: secret,
            user: $username,
            time: new Date().toISOString()
            });
        const itemname = new Date().toISOString();
        db.get('chatMiyagami').get(itemname).put(message)

    }

        // encrypt messages

    // function to get more messages

</script>

<div>
    {#if $username}
        {#each messages as message}
            <Message {message} />
        {/each}
        <div class="fixed absolute bottom-0">
            <form on:submit|preventDefault={submitMessage}>
                <input bind:value={newMessage}/>
                <button type="submit">say</button>
            </form>
        </div>
    {:else}
        <Login />
    {/if}
</div>
