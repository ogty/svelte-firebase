<script lang="ts">
    import { Router, Link, Route } from "svelte-routing";
	import Home from "./pages/Home.svelte";
    import { initializeApp }  from 'firebase/app';

	const firebaseConfig = {
        apiKey: "AIzaSyApoCd_j5OKnskS1CFSidlmeCEBCpB2oKM",
        authDomain: "test-2b296.firebaseapp.com",
        projectId: "test-2b296",
        storageBucket: "test-2b296.appspot.com",
        messagingSenderId: "496593764890",
        appId: "1:496593764890:web:0a4053a50b394b6ed107a3",
        measurementId: "${config.measurementId}"
	}
	
	initializeApp(firebaseConfig);
</script>

<Router>
    <header>
        <Link to=""></Link>
        <Route path="/" component={Home} />
    </header>
</Router>

<style global lang="postcss">
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
</style>