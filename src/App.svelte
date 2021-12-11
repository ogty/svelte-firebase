<script lang="ts">
    import { Router, Link, Route } from "svelte-routing";
	import Home from "./pages/Home.svelte";
    import { initializeApp }  from 'firebase/app';

	const firebaseConfig = {
		apiKey: "AIzaSyAHITlgmcGGQ6jADHvLFzWdTBITKV1FiEI",
	  authDomain: "svelte-fire-tail-temp.firebaseapp.com",
	  projectId: "svelte-fire-tail-temp",
	  storageBucket: "svelte-fire-tail-temp.appspot.com",
	  messagingSenderId: "117783386320",
	  appId: "1:117783386320:web:fdec9fe8372b4c7e9ee6d5"
	};
	
	initializeApp(firebaseConfig);
</script>

<Router>
	<Link to=""></Link>
	<Route path="/" component={Home} />
</Router>

<style global lang="postcss">
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
</style>