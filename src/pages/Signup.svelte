<script lang="ts">
    import { getAuth, createUserWithEmailAndPassword, signInWithEmailAndPassword } from "firebase/auth";
    export let loginWithGoogle

    let email = ""
    let password = ""

    const auth = getAuth();

    function createCall() {
        createUserWithEmailAndPassword(auth, email, password)
    .then((userCredential) => {
        // Signed in
        const user = userCredential.user;
        // ...
    })
    .catch((error) => {
        const errorCode = error.code;
        const errorMessage = error.message;
        // ..
    });
    }


    function signInCall() {
        signInWithEmailAndPassword(auth, email, password)
        .then((userCredential) => {
            // Signed in
            const user = userCredential.user;
            console.log(user)
            // ...
        })
        .catch((error) => {
            const errorCode = error.code;
            const errorMessage = error.message;
        });
    }
</script>

<div class="popup_wrap">
    <input id="trigger" type="checkbox" style="display: none;">
    <div class="popup_overlay">
        <label for="trigger" class="popup_trigger"></label>
        <div class="popup_content">
            <div class="fixed z-10 inset-0 overflow-y-auto" aria-labelledby="modal-title" role="dialog" aria-modal="true">
                <div class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">
                <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" aria-hidden="true"></div>
                    <span class="hidden sm:inline-block sm:align-middle sm:h-screen" aria-hidden="true">&#8203;</span>
                    <div class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full">
                    <div style="height: 60px;"></div>
                        <div class="bg-grey-lighter h-auto flex flex-col">
                            <div class="container max-w-sm mx-auto flex-1 flex flex-col items-center justify-center px-2">
                                <div class="bg-white px-6 py-8 rounded shadow-md text-black w-full">
                                    <h1 class="mb-8 text-3xl text-center">Sign up</h1>
                                    <div on:click={loginWithGoogle} style="cursor: pointer;" id="google_button" class="border-4 border-zinc-600 py-3 rounded-lg transform motion-reduce:transform-none hover:-translate-y-1 hover:scale-10 transition ease-in-out duration-300">
                                        <span class=" landing_form--googleIcon--3Q7rS">
                                            <svg class="svg" width="18" height="18" viewBox="0 0 18 18" xmlns="http://www.w3.org/2000/svg">
                                                <path d="M17.64 9.2c0-.637-.057-1.251-.164-1.84H9v3.481h4.844c-.209 1.125-.843 2.078-1.796 2.717v2.258h2.908c1.702-1.567 2.684-3.874 2.684-6.615z" fill-rule="evenodd" fill-opacity="1" fill="#4285f4" stroke="none"></path>
                                                <path d="M9.003 18c2.43 0 4.467-.806 5.956-2.18L12.05 13.56c-.806.54-1.836.86-3.047.86-2.344 0-4.328-1.584-5.036-3.711H.96v2.332C2.44 15.983 5.485 18 9.003 18z" fill-rule="evenodd" fill-opacity="1" fill="#34a853" stroke="none"></path><path d="M3.964 10.712c-.18-.54-.282-1.117-.282-1.71 0-.593.102-1.17.282-1.71V4.96H.957C.347 6.175 0 7.55 0 9.002c0 1.452.348 2.827.957 4.042l3.007-2.332z" fill-rule="evenodd" fill-opacity="1" fill="#fbbc05" stroke="none"></path><path d="M9.003 3.58c1.321 0 2.508.454 3.44 1.345l2.582-2.58C13.464.891 11.428 0 9.002 0 5.485 0 2.44 2.017.96 4.958L3.967 7.29c.708-2.127 2.692-3.71 5.036-3.71z" fill-rule="evenodd" fill-opacity="1" fill="#ea4335" stroke="none"></path>
                                            </svg>
                                        </span>
                                        <a href="#" style="margin-left: 10px;">
                                            <span class="text-zinc-900">Continue to Google</span>
                                        </a>
                                    </div>
                                    <div class="w-full text-center py-3">
                                        or
                                    </div>
                                    <input value={email} type="text" class="block border border-grey-light w-full p-3 rounded mb-4" name="email" placeholder="Email" />
                                    <input type="password" class="block border border-grey-light w-full p-3 rounded mb-4" name="password" placeholder="Password" />
                                    <input value={password} type="password" class="block border border-grey-light w-full p-3 rounded mb-4" name="confirm_password" placeholder="Confirm Password" />
                                    <button type="submit" class="transform motion-reduce:transform-none hover:-translate-y-1 hover:scale-10 transition ease-in-out duration-300 w-full text-center py-3 rounded-lg bg-zinc-900 text-white hover:bg-green-dark focus:outline-none my-1">Create Account</button>
                                    <div class="text-center text-sm text-grey-dark mt-4">
                                        By signing up, you agree to the 
                                        <a class="no-underline border-b border-grey-dark text-grey-dark" href="/">Terms of Service </a> 
                                        and 
                                        <a class="no-underline border-b border-grey-dark text-grey-dark" href="/">Privacy Policy</a>
                                    </div>
                                </div>
                                <div class="text-grey-dark mt-6 ">
                                    Already have an account?
                                    <a class="no-underline border-b border-blue text-blue " href="/"> Log in</a>.
                                </div>
                            </div>
                        </div>
                        <div style="height: 40px;">
                            <label for="trigger" class="close_btn">×</label>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>