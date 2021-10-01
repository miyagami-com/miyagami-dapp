<script>
import { username,user } from './user'

function signout() {
    user.leave();
    username.set("")

}

</script>

<!--<header>-->
<!--    <h1>Miyagami Chat App</h1>-->
<!--    {#if $username}-->
<!--    <div clas="user-bio">-->
<!--        <span>Hello <strong>{$username}</strong></span>-->
<!--        &lt;!&ndash; <img src={`https://avatars.dicebear.com/api/initials/${$username}.svg`}/> &ndash;&gt;-->
<!--    </div>-->

<!--    <button class="rounded-md" on:click={signout}>-->
<!--        Sign Out-->
<!--    </button>-->
<!--    {:else}-->
<!--    <h3>Miyagami Chat</h3>-->
<!--    {/if}-->
<!--</header>-->

<!-- This example requires Tailwind CSS v2.0+ -->
<div class="relative bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6">
        <div class="flex justify-between items-center border-b-2 border-gray-100 py-6 md:justify-start md:space-x-10">
            <div class="flex justify-start lg:w-0 lg:flex-1">
                <a href="#">
                    <span class="sr-only">Workflow</span>
                    <img class="h-8 w-auto sm:h-10" src="https://tailwindui.com/img/logos/workflow-mark-indigo-600.svg" alt="">
                </a>
            </div>
            <div class="-mr-2 -my-2 md:hidden">
                <button type="button" class="bg-white rounded-md p-2 inline-flex items-center justify-center text-gray-400 hover:text-gray-500 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-500" aria-expanded="false">
                    <span class="sr -only">Login</span>
                </button>
            </div>
            <div class="hidden md:flex items-center justify-end md:flex-1 lg:w-0">
                <a href="#" class="whitespace-nowrap text-base font-medium text-gray-500 hover:text-gray-900">
                    Sign in
                </a>
                <a href="#" class="ml-8 whitespace-nowrap inline-flex items-center justify-center px-4 py-2 border border-transparent rounded-md shadow-sm text-base font-medium text-white bg-indigo-600 hover:bg-indigo-700">
                    Sign up
                </a>
            </div>
        </div>
    </div>
</div>
