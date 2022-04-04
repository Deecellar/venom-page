<script lang="ts">
	import ModeSwitcher from "./ModeSwitcher.svelte";
	import Tailwindcss from "./Tailwindcss.svelte";
	import { Router, Route } from "svelte-routing";
	import Home from "./routes/Home.svelte";
	import About from "./routes/About.svelte";
	import Contact from "./routes/Contact.svelte";
	import Download from "./routes/Download.svelte";
	import Wiki from "./routes/Wiki.svelte";
	import NavBar from "./components/NavBar.svelte";
	import Footer from "./components/Footer.svelte";

	export let url: string;
</script>
<svelte:head>
	
</svelte:head>
<Tailwindcss />
<ModeSwitcher />
<main>
	<Router {url}>
		<NavBar />
		<Route path="/" component={Home} />
		<Route path="/downloads" component={Download} />
		<Route path="/wiki" component={Wiki} />
		<Route path="/about" component={About} />
		<Route path="/contact" component={Contact} />
	</Router>
	<Footer />
</main>
