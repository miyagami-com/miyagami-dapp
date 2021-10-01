<script>
    import {banner} from './user'

    function onClick() {
        banner.set(false)
    }
</script>

{#if $banner}
    <div class="relative bg-red-600 rounded-md">
        <div class="max-w-7xl mx-auto py-3 px-3 sm:px-6 lg:px-8 ">
            <div class="pr-16 sm:text-center sm:px-16">
                <p class="font-medium text-white">
                    <span class="inline">
                        Free End-to-end encrypted decentralized chat room!
                    </span>
                    <span class="block sm:ml-2 sm:inline-block">
                      <a href="https://miyagami.com/contact" target="_blank"
                         class="text-white hover:text-white visited:text-white active:text-white">
                          Learn more <span aria-hidden="true">&rarr;</span>
                      </a>
                    </span>
                </p>
            </div>
            <div class="absolute inset-y-0 right-0 pt-1 pr-1 flex items-start sm:pt-1 sm:pr-2 sm:items-start self-center">
                <button
                    type="button"
                    on:click={onClick}
                    class="flex p-2 rounded-md hover:bg-red-500 focus:outline-none focus:ring-2 focus:ring-white"
                >
                    <svg class="h-4 w-4 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                         stroke="currentColor" aria-hidden="true">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
                    </svg>
                </button>
            </div>
        </div>
    </div>
{/if}
