<script>
    import { username } from './user'

    export let message;

    let sent = "sm:flex sm:justify-between sm:items-baseline bg-red-100 flex-row-reverse"
    let received = "bg-white-100 "

    const messageClass = message.user === $username ? sent : received;

    console.log(message.user, $username)

    const ts = new Date(message.time);

  

  </script>


  <div class={messageClass}>
    <div>
      <p class="text-gray-600">{message.text}</p>
      <time>{ts.toLocaleTimeString()}</time>
    </div>
  </div>


