<script>
import { username,user } from './user'

function signOut() {
    user.leave();
    username.set("")
}
</script>

<div class="relative bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6">
        <div class="flex justify-start items-center border-b-2 border-gray-100 py-6 xs:space-between space-x-4">
            {#if $username}
            <div class="flex justify-start lg:w-0 ">
                <a href="/">
                    <img class="h-10 w-auto" src={`https://avatars.dicebear.com/api/initials/${$username}.svg`} alt="">
                </a>
            </div>
            <h3 class="text-center text-2xl font-extrabold text-gray-900">
                {$username}
            </h3>
            <div class="flex items-center justify-end md:flex-1 lg:w-0">
                <a on:click={signOut} class="ml-8 whitespace-nowrap inline-flex items-center justify-center px-4 py-2 border border-transparent rounded-md shadow-sm text-base font-medium text-white bg-red-600 hover:bg-red-700">
                    Sign out
                </a>
            </div>
            {:else}
            <div class="flex justify-start">
                <a href="/">
                    <img class="h-10 w-auto" src="/miyagami-logo.png" alt="">
                </a>
            </div>
            <h3 class="text-center xs:text-lg text-2xl font-extrabold text-gray-900">
                Miyagami Chat
            </h3>
            {/if}
        </div>
    </div>
</div>
