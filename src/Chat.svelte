<script>
    import {username} from './user'
    import GUN from 'gun';
    import 'gun/sea';
    import 'gun/axe';
    import {onMount} from 'svelte';
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

        db.get('chatMiyagami').map().once(async (data) => {
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
</script>

<div class="">
    {#if $username}
        <div class="p-4 max-w-lg mx-auto">
        {#each messages as message}
            <Message {message}/>
        {/each}
        </div>
        <div class="sticky left-0 bottom-0 bg-white w-full border-t-2 border-gray-100">
            <form class="p-4 max-w-lg mx-auto" on:submit|preventDefault={submitMessage}>
                <div>
                    <label for="newMessage" class="block text-sm font-medium text-gray-700">Message</label>
                    <div class="mt-1 flex rounded-md shadow-sm">
                        <div class="relative flex items-stretch flex-grow focus-within:z-10">
                            <input type="text" bind:value={newMessage} name="newMessage" id="newMessage"
                                   class="focus:ring-red-500 focus:border-red-500 block w-full rounded-none pl-3 rounded-l-md sm:text-sm border-gray-300"
                                   placeholder="Send a message to the chat!">
                        </div>
                        <button type="submit"
                                class="-ml-px relative inline-flex items-center space-x-2 px-4 py-2 border border-gray-300 text-sm font-medium rounded-r-md text-gray-700 bg-gray-50 hover:bg-gray-100 focus:outline-none focus:ring-1 focus:ring-red-500 focus:border-red-500">
                            <span>Send</span>
                        </button>
                    </div>
                </div>
            </form>
        </div>
    {:else}
        <Login/>
    {/if}
</div>
