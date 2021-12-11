<script lang="ts">
    export let logOut;
    export let userIconURL = "";
</script>

<button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" on:click={logOut}>Log out</button>
<img class="rounded-full" src="{userIconURL}" alt="user-img">
