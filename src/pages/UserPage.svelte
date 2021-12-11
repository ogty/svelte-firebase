<script lang="ts">
    import DeleteUser from './DelteUser.svelte'
    export let logOut;
    export let userIconURL;
</script>


<div class="flex justify-between bg-zinc-800 -m-2 p-2">
    <div class="order-last flex flex-row">
        <img class="rounded-full" src="{userIconURL}" alt="user-img">
        <svg width="8" height="6" viewBox="0 0 8 6" class="text-white h-10" style="margin-left: 10px;"><path d="M4 6L0.535898 0L7.4641 0L4 6Z" fill="currentColor"></path></svg>
    </div>
    <div></div>
    <div></div>
</div>

<div class="h-20"></div>

<a href="/" class="font-bold" on:click={logOut}>
    <span class="text-slate-900">Log out</span>
</a>

<DeleteUser />
<style>
    img {
        width: 35%;
    }
</style>