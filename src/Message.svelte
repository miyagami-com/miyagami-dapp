<script>
    import {username} from './user'

    export let message;

    const messageClass = message.user === $username;

    const ts = new Date(message.time);


</script>

{#if message.user === $username}
  <div class="my-2 flex flex-col items-end">
    <div class="bg-red-100 shadow-md px-4 py-2 my-1 rounded-2xl flex flex-col text-right">
      <span class="text-red-800 font-semibold">{$username}</span>
      {message.text}
    </div>
    <time class="mr-2">{ts.toLocaleTimeString()}</time>
  </div>
{:else}
  <div class="my-2 flex flex-col items-start">
    <div class="bg-white shadow-md px-4 py-2 my-1 rounded-2xl flex flex-col text-left">
      <span class="font-semibold">{message.user}</span>
      {message.text}
    </div>
    <time class="ml-2">{ts.toLocaleTimeString()}</time>
  </div>
{/if}




