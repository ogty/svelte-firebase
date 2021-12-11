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


<button on:click={deleteCall}>退会する</button>