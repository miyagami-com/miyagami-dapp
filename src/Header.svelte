<script>
import { username,user } from './user'

function signout() {
    user.leave();
    username.set('')
}

</script>

<header>
    <h1>Miyagami Chat App</h1>
    {#if $username}
    <div clas="user-bio">
        <span>Hello <strong>{$username}</strong></span>
        <!-- <img src={`https://avatars.dicebear.com/api/initials/${$username}.svg`}/> -->
    </div>

    <button class="rounded-md" on:click={signout}>
        Sign Out
    </button>

    {:else}
    <h3>Miyagami Chat</h3>
    {/if}
</header>