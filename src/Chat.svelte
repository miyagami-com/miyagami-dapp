<script>
    import { username } from './user'
    import GUN from 'gun';
    import 'gun/sea';
    import 'gun/axe';
    import { onMount } from 'svelte';

    let newMessage = '';
    let messages = []
    const db = GUN();
    let key = "thisisthekey"

    // Define db
    onMount(() => {
        db.get('chatMiyagami').map().once( async (data) => {        

        var message = {
            text: (await SEA.decrypt(data.text, key)) + '',
            user: $username,
            time: GUN.state.is(data, 'text')
        }
        messages = [...messages.slice(-5), message]

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

<form on:submit|preventDefault={submitMessage}>
    <input bind:value={newMessage}/>
    <button type="submit">say</button>
</form>
{#each messages as message}
   <p> User: {message.user}</p>
   <p> {message.text}</p>
   <p> {message.time}</p>
{/each}

