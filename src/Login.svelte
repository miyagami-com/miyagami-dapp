<script>
    import { user } from "./user";

    let username;
    let password;

    function login() {
        user.auth(username.toLowerCase(), password, ({err}) => err && alert(err));
    }

    function signUp() {
        user.create(username.toLowerCase(), password, ({err}) => {
            if(err){
                alert(err)
            }else{
                login()
            }
        });
    }

</script>


<div class="flex flex-col justify-center py-8 sm:px-6 lg:px-8">
    <div class="sm:mx-auto sm:w-full sm:max-w-md">
        <h2 class="mt-6 text-center text-2xl font-extrabold text-gray-900">
            Sign in to your account
        </h2>
    </div>

    <div class="mt-8 sm:mx-auto sm:w-full sm:max-w-md">
        <div class="bg-white py-8 px-4 shadow sm:rounded-lg sm:px-10">
            <div class="space-y-6">
                <div>
                    <label for="username" class="block text-sm font-medium text-gray-700">
                       Username
                    </label>
                    <div class="mt-1">
                        <input bind:value={username} autocomplete="username" id="username" name="username" type="text" required class="appearance-none block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm placeholder-gray-400 focus:outline-none focus:ring-red-500 focus:border-red-500 sm:text-sm">
                    </div>
                </div>

                <div>
                    <label for="password" class="block text-sm font-medium text-gray-700">
                        Password
                    </label>
                    <div class="mt-1">
                        <input bind:value={password} id="password" name="password" type="password" autocomplete="current-password" required class="appearance-none block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm placeholder-gray-400 focus:outline-none focus:ring-red-500 focus:border-red-500 sm:text-sm">
                    </div>
                </div>
                <div>
                    <button on:click={login} class="w-full flex justify-center py-2 px-4 border border-transparent rounded-md shadow-md text-sm font-medium text-white bg-red-600 hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500">
                        Login
                    </button>
                </div>
                <div>
                    <button on:click={signUp} class="w-full flex justify-center py-2 px-4 border border-grey-50 rounded-md shadow-md text-sm font-medium text-red-600 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500">
                        Sign up
                    </button>
                </div>
            </div>
        </div>
    </div>
    <p class="mt-4 text-center no-underline	">Created with ❤️ by <a href="https://miyagami.com" target="_blank">Miyagami</a></p>
</div>
