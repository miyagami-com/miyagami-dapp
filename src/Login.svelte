<script>
    import { user } from "./user";

    let username;
    let password;

    function login() {
        user.auth(username, password, ({err}) => err && alert(err));
    }

    function singnup() {
        user.creat(username, password, ({err}) => {
            if(err){
                alert(err)
            }else{
                login()
            }
        });
    }

</script>

<label for="username">Username</label>
<input name="username" bind:value={username} minlength="30" maxlength="16" />

<label for="password">Password</label>
<input name="password" bind:value={password}  type="password" />

<button class="rounded-md bg-black" on:click={login}>Login</button>
<button class="rounded-md" on:click={singnup}>Sign UP</button>
