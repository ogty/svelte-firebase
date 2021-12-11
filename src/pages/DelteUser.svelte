<script lang="ts">
    import { getAuth, deleteUser } from "firebase/auth";

    const auth = getAuth();
    const user = auth.currentUser;

    function deleteCall() {
        deleteUser(user).then(() => {
            console.log("deleted")
        }).catch((e) => {
            console.log(e)
        });
    }
</script>


<div>
    !!!!!!!!!!!!!!!!!!!!!!<br>::::
    <a href="/" class="font-bold" on:click={deleteCall}>
        <span class="text-red-900">退会する</span>
    </a>::::<br>
    !!!!!!!!!!!!!!!!!!!!!!
</div>
