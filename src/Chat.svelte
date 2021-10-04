<script>
    import {username, user} from './user'
    import GUN from 'gun';
    import 'gun/sea';
    import 'gun/axe';
    import {onMount} from 'svelte';
    import Message from './Message.svelte'
    import Login from "./Login.svelte";

    const peer = GUN_PEER;
    const key = AES_KEY;
    const db = GUN({peers: [peer, 'https://gun-chat-dapp.web.app/gun', 'https://miyagami-dapp.vercel.app/gun']});

    let newMessage = '';
    let messages = []

    // Define db
    onMount(() => {
        let match = {
            // lexical queries are kind of like a limited RegEx or Glob.
            '.': {
                // property selector
                '>': new Date(+new Date() - 1000 * 60 * 60 * 3).toISOString(), // find any indexed property larger ~3 hours ago
            },
            '-': 1, // filter in reverse
        };

        db.get('chat')
            .map(match)
            .once(async (data) => {
                if (data) {
                    let message = {
                        what: (await SEA.decrypt(data.what, key)) + '',
                        who: await db.user(data).get('alias'),
                        when: GUN.state.is(data, 'what')
                    }
                    if (message.what) {
                        messages = [...messages.slice(-100), message].sort((a, b) => a.when - b.when);
                    }
                }
            });

    })

    // function to create/send message
    async function submitMessage() {
        const secret = await SEA.encrypt(newMessage, key);
        const message = user.get('all').set({
            what: secret,
        });
        const index = new Date().toISOString();
        db.get('chat').get(index).put(message)
        newMessage = '';
    }
</script>

<div>
    {#if $username}
        <div class="p-4 max-w-lg mx-auto flex flex-col chat ">
            {#each messages as message (message.when)}
                <Message {message} sender="{$username}"/>
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
