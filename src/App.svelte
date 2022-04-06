<script lang="ts">
	import ModeSwitcher from "./ModeSwitcher.svelte";
	import Tailwindcss from "./Tailwindcss.svelte";
	import { Router, Route } from "svelte-routing";
	import Home from "./routes/Home.svelte";
	import Download from "./routes/Download.svelte";
	import Wiki from "./routes/Wiki.svelte";
	import NavBar from "./components/NavBar.svelte";
	import Footer from "./components/Footer.svelte";
	const isGithubPages = true; // put it in true when you are deploying to a github pages URL
	const webpageGithub = "venom-page";
	export let url: string;
</script>

<svelte:head />
<Tailwindcss />
<ModeSwitcher />
<main>
	<div class="flex flex-col h-screen">
		<div class="flex-grow">
			<Router {url}>
				<NavBar />
				<div class="mt-6">
					<Route
						path="{isGithubPages ? '/' + webpageGithub : ''}/"
						component={Home}
					/>
					<Route
						path="{isGithubPages
							? '/' + webpageGithub
							: ''}/downloads"
						component={Download}
					/>
					<Route
						path="{isGithubPages ? '/' + webpageGithub : ''}/wiki"
						component={Wiki}
					/>
				</div>
			</Router>
		</div>

		<Footer />
	</div>
</main>
