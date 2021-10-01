<script>
    import { username } from './user'

    export let message;
    const messageClass = message.user === $username ? 'sent' : 'received';
    console.log(message.user, $username)

    const ts = new Date(message.time);
  </script>

  <div class={`message ${messageClass}`}>
    <div class="message-text">
      <p>{message.text}</p>

      <time>{ts.toLocaleTimeString()}</time>
    </div>
  </div>
