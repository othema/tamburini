<script lang="ts">
	import { page } from "$app/stores";
	import { fade } from "svelte/transition";

	export let links: { name: string; href: string }[] = [];
	export let image: string;
	export let title: string;

	let linkIndex = links.findIndex((link) => link.href === $page.url.pathname);
	let leftLink = links[(linkIndex - 1 + links.length) % links.length];
	let rightLink = links[(linkIndex + 1) % links.length];
</script>

<article class="grid h-full grid-cols-3 grid-rows-3 divide-y divide-x divide-gray-800">
	<div class="h-full col-span-2 row-span-2 bg-[image:var(--image-url)] bg-cover lg:bg-[0_-150px] xl:bg-[0_-250px] bg-no-repeat" style="--image-url: url({image})"></div>
	<div class="h-full col-span-1 row-span-2 !border-t-0 text-zinc-500 font-mono text-lg leading-relaxed p-16 flex flex-col justify-end">
		<slot />
	</div>
	<div class="h-full col-span-2 flex items-center px-20">
		<h2 class="text-gray-200 font-display font-black uppercase text-5xl max-w-xl">{title}</h2>
	</div>
	<div class="h-full col-span-1 flex text-gray-200 divide-x divide-gray-800">
		<a class="flex-1 flex justify-center items-center group" href={leftLink.href}>
			<svg class="w-14 h-14 group-hover:-translate-x-6 duration-200" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
				<path stroke-linecap="round" stroke-linejoin="round" d="M6.75 15.75L3 12m0 0l3.75-3.75M3 12h18" />
			</svg>
		</a>
		<a class="flex-1 flex justify-center items-center group" href={rightLink.href}>
			<svg class="w-14 h-14 group-hover:translate-x-6 duration-200" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
				<path stroke-linecap="round" stroke-linejoin="round" d="M17.25 8.25L21 12m0 0l-3.75 3.75M21 12H3" />
			</svg>
		</a>
	</div>
</article>
