<script>
    import { user, username } from "./user";

    let username_val;
    let password_val;

    function login() {
        user.auth(username_val, password_val, ({err}) => err && alert(err));
    }

    function signup() {
        user.create(username_val, password_val, ({err}) => {
            if(err){
                alert(err)
            }else{
                login()
            }
        });
    }

</script>

<label for="username">Username</label>
<input name="username" bind:value={username_val} minlength="30" maxlength="16" />

<label for="password">Password</label>
<input name="password" bind:value={password_val}  type="password" />

<button class="rounded-md bg-black" on:click={login}>Login</button>
<button class="rounded-md" on:click={signup}>Sign UP</button>
