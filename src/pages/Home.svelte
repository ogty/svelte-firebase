<script lang="ts">
    import * as firebaseAuth from 'firebase/auth'
    import UserPage from './UserPage.svelte';
    import About from './About.svelte';

    const auth = firebaseAuth.getAuth();
    let isUser = false
    let userIconURL = ""

    firebaseAuth.onAuthStateChanged(auth, (user) => {
        if (user) {
            const displayName = user.displayName;
            const photoURL = user.photoURL;

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
            const provider = new firebaseAuth.GoogleAuthProvider();
            await firebaseAuth.signInWithPopup(auth, provider);
            // await signInWithRedirect(auth, provider);
            console.log("Success!!")
        } catch (e) {
            console.log(e);
        }
    }

    async function logOut() {
        try {
            await firebaseAuth.signOut(auth)
            location.reload()
        } catch (e) {
            console.log(e);
        }
    }
</script>

{#if isUser}
    <UserPage {logOut} {userIconURL} />
{:else}
    <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" on:click={loginWithGoogle}>Log in</button>
    <About />
{/if}