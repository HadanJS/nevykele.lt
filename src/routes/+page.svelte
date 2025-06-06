<script>
	import { onMount } from 'svelte';
	import { scale } from 'svelte/transition';

	let isPopupVisible = false;

	onMount(() => {
		const timer = setTimeout(() => {
			isPopupVisible = true;
		}, 3000);
		return () => clearTimeout(timer);
	});

	function closePopup() {
		isPopupVisible = false;
	}
</script>

<div class="relative w-screen h-screen overflow-hidden">
	<img class="w-full h-full object-cover" src="/banner.png" alt="Background banner" />

	{#if isPopupVisible}
		<div
			class="fixed inset-0 flex items-center justify-center bg-black/50 backdrop-blur-sm"
			transition:scale="{{ duration: 200, start: 0, opacity: 0 }}"
		>
			<div class="relative">
				<a
					href="https://www.youtube.com/watch?v=_tfoD2Akx2s&t=11s"
					class="relative block transform transition-transform hover:scale-105 focus:scale-105 outline-none"
					aria-label="Navigate to YouTube video"
				>
					<img
						src="/popup.png"
						alt="Popup content"
						class="max-w-[600px] object-contain rounded-lg shadow-2xl"
					/>
				</a>
				<button
					on:click={closePopup}
					class="absolute top-2 right-2 text-white font-bold bg-black/40 cursor-grab rounded-full w-8 h-8 flex items-center justify-center focus:outline-none"
					aria-label="Close popup"
				>
					<span class="text-xl">×</span>
				</button>
			</div>
		</div>
	{/if}
</div>

<style>
	:global(body) {
		margin: 0;
	}
</style>