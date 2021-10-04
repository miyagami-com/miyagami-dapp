<script>
import { username, user } from './user'

function signOut() {
    user.leave();
    username.set("")
}
</script>

<div class="bg-white fixed left-0 top-0 z-50 w-full">
    <div class="max-w-lg mx-auto px-4">
        <div class="flex border-b-2 border-gray-100 py-6 justify-between space-x-4">
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
                <button on:click={signOut} class="ml-8 whitespace-nowrap inline-flex items-center justify-center px-4 py-2 border border-transparent rounded-md shadow-sm text-base font-medium text-white bg-red-600 hover:bg-red-700">
                    Sign out
                </button>
            </div>
            {:else}
            <div class="flex justify-center">
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
