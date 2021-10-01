<script>
    import { username,user } from './user'
 //   import {messages} from './store.js'
    import GUN from 'gun';
    import 'gun/sea';
    import 'gun/axe';
    import {writable} from 'svelte/store'
    import { onMount } from 'svelte';

    let message = '';
    let messages = []
    const db = GUN();
    
    // Define db
    onMount(() => {

        db.get('chatmiyagami').map().once( async (v) => {
        console.log(v)
        console.log("added")
        // $messages = [...$messages, v]
        // console.log($messages);
        messages = [...messages.slice(-100), v]
        console.log(messages);
        });

    })
    // get messages (limit?)

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

<label>Username</label>
<label>Username</label>
<form on:submit|preventDefault={submitMessage}>
    <input bind:value={message}/>
    <button type="submit">say</button>
</form>
{#each messages as message}
   <p> User: {message.user}</p>
   <p> {message.text}</p>
   <p> {message.time}</p>
{/each}

