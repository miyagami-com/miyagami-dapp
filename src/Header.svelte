<script>
import { username, user } from './user'

function signOut() {
    user.leave();
    username.set("")
}
</script>

<div class="relative bg-white">
    <div class="max-w-7xl mx-auto px-4">
        <div class="flex md:justify-center items-center border-b-2 border-gray-100 py-6 justify-between space-x-4">
            {#if $username}
            <div class="flex justify-start">
                <a href="/">
                    <img class="h-10 w-auto rounded-full mr-3" src={`https://avatars.dicebear.com/api/initials/${$username}.svg`} alt="">
                </a>
                <h3 class="text-center text-2xl font-extrabold text-gray-900 self-center">
                    {$username}
                </h3>
            </div>
            <div class="flex items-center justify-end">
                <a on:click={signOut} class="ml-8 whitespace-nowrap inline-flex items-center justify-center px-4 py-2 border border-transparent rounded-md shadow-sm text-base font-medium text-white bg-red-600 hover:bg-red-700">
                    Sign out
                </a>
            </div>
            {:else}
            <div class="flex justify-start">
                <a href="/">
                    <img class="h-10 w-auto rounded-full mr-3" src="/miyagami-logo.png" alt="">
                </a>
                <h3 class="text-center text-2xl font-extrabold text-gray-900 self-center">
                    Miyagami Chat
                </h3>
            </div>
            {/if}
        </div>
    </div>
</div>
