<script>
  import "../app.css";
	import { page } from "$app/stores";
	import { fade } from "svelte/transition";

	export let data;
	const links = [{href: "/", name: "Home"}, {href: "/negatives", name: "Negatives"}, {href: "/positives", name: "Positives"}];
</script>

<div class="bg-gray-950 min-h-screen">
	<div class="flex flex-col h-screen">
		<nav class="flex border-b border-gray-800 divide-x divide-gray-800 font-mono font-medium text-zinc-600 items-center">
			<div class="px-12 py-8 flex basis-1/3 text-gray-200 text-xl uppercase font-display font-black">Alex Tamburini</div>
			
			<div class="px-12 py-8 flex basis-1/3 justify-around uppercase">
				{#each links as link}
					<a href={link.href} class="{$page.url.pathname === link.href ? 'text-indigo-400 hover:text-indigo-300 opacity-80' : 'hover:text-zinc-500'} duration-150">{link.name}</a>
				{/each}
			</div>

			<div class="px-12 py-8 flex flex-grow justify-around">
				<a href="https://www.instagram.com/tamb0urinee/" target="_blank">
					<svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 hover:stroke-indigo-400 hover:opacity-80 duration-150" viewBox="0 0 24 24" stroke-width={1.5} stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
						<path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
						<path d="M4 4m0 4a4 4 0 0 1 4 -4h8a4 4 0 0 1 4 4v8a4 4 0 0 1 -4 4h-8a4 4 0 0 1 -4 -4z"></path>
						<path d="M12 12m-3 0a3 3 0 1 0 6 0a3 3 0 1 0 -6 0"></path>
						<path d="M16.5 7.5l0 .01"></path>
					</svg>
				</a>

				<a href="https://www.facebook.com/alex.tamburini.5" target="_blank">
					<svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 hover:stroke-indigo-400 hover:opacity-80 duration-150" viewBox="0 0 24 24" stroke-width={1.5} stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
						<path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
						<path d="M7 10v4h3v7h4v-7h3l1 -4h-4v-2a1 1 0 0 1 1 -1h3v-4h-3a5 5 0 0 0 -5 5v2h-3"></path>
					</svg>
				</a>

				<button on:click={() => alert("+447983659745 💀")}>
					<svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 hover:stroke-indigo-400 hover:opacity-80 duration-150" viewBox="0 0 24 24" stroke-width={1.8} stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
						<path stroke="none" d="M0 0h24v24H0z" fill="none"></path>
						<path d="M3 21l1.65 -3.8a9 9 0 1 1 3.4 2.9l-5.05 .9"></path>
						<path d="M9 10a.5 .5 0 0 0 1 0v-1a.5 .5 0 0 0 -1 0v1a5 5 0 0 0 5 5h1a.5 .5 0 0 0 0 -1h-1a.5 .5 0 0 0 0 1"></path>
					</svg>
				</button>
			</div>

			<div class="px-12 py-8 flex flex-grow justify-center">
				<button on:click={() => alert("+447983659745 💀")} class="uppercase hover:text-indigo-400 hover:opacity-80 duration-150">Get in touch</button>
			</div>
		</nav>

		<main class="h-full overflow-hidden">
			{#key data.url}
				<div in:fade={{ duration: 200, delay: 200 }} out:fade={{ duration: 200 }} class="h-full">
					<slot />
				</div>
			{/key}
		</main>
	</div>
</div>

