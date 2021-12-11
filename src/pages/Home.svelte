<script lang="ts">
    import * as firebaseAuth from 'firebase/auth'
    import UserPage from './UserPage.svelte'
    import About from './About.svelte'

    const auth = firebaseAuth.getAuth()
    let isUser = false
    let userIconURL = ""

    firebaseAuth.onAuthStateChanged(auth, (user) => {
        if (user) {
            const displayName = user.displayName
            const photoURL = user.photoURL

            console.log(displayName)
            console.log(photoURL)
            userIconURL = photoURL
            isUser = true
        } else {
            console.log("Not log inned")
        }
    });

    async function loginWithGoogle() {
        try {
            const provider = new firebaseAuth.GoogleAuthProvider()
            // await firebaseAuth.signInWithPopup(auth, provider);
            await firebaseAuth.signInWithRedirect(auth, provider)
            console.log("Success!!")
        } catch (e) {
            console.log(e)
        }
    }

    async function logOut() {
        try {
            await firebaseAuth.signOut(auth)
            location.reload()
        } catch (e) {
            console.log(e)
        }
    }
</script>

    
{#if isUser}
    <UserPage {logOut} {userIconURL} />
{:else}
    <header class="text-gray-100body-font w-full h-100">
        <div class="container mx-auto flex flex-wrap p-5 flex-col md:flex-row items-center">
            <a href="/" class="text-2xl">Logo Space</a>
            <nav class="flex lg:w-2/5 flex-wrap items-center text-base md:ml-auto">
            </nav>
            <div class="lg:w-2/5 inline-flex lg:justify-end ml-5 lg:ml-0">
                <a href="/" class="ml-4 py-2 px-3 font-bold">
                    <span class="text-slate-900">Company</span>
                </a>
                <a href="/" class="ml-4 py-2 px-3 font-bold">
                    <span class="text-slate-900">Pricing</span>
                </a>
                <a href="#" class="ml-4 py-2 px-3 font-bold" on:click={loginWithGoogle}>
                    <span class="text-slate-900">Log in</span>
                </a>
                <a href="/" class="no-underline transform motion-reduce:transform-none hover:-translate-y-1 hover:scale-110 transition ease-in-out duration-300 bg-zinc-900 font-bold ml-4 py-2 px-3 rounded-lg">
                    <span class="text-white">Sign up</span>
                </a>
            </div>
        </div>
    </header>
    <About />
{/if}