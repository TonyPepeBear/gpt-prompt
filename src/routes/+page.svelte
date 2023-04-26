<script lang="ts">
	import rawData from '../data/prompts.json';
	import IconPen from '$lib/components/svg/IconPen.svelte';
	import IconClipboard from '$lib/components/svg/IconClipboard.svelte';
	var data = rawData;
	function copyToClipboard(prompt: string, firstPrompt: string) {
		navigator.clipboard.writeText(prompt + '\n\n我的第一個指令是：' + firstPrompt);
	}
</script>

<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="true" />
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+TC&display=swap" rel="stylesheet" />

<div class="u-mx-1 md:u-mx-10 lg:u-mx-20 xl:u-mx80">
	<h1 class="u-text-8">ChatGPT 咒文指南</h1>
	<p class="u-text-4.5">
		ChatGPT是一個基於GPT-3.5架構訓練的大型語言模型，可以回答各種問題和提供各種建議。但是，有些使用者可能會發現和
		ChatGPT 對話時有些困難或不順暢。ChatGPT
		咒文指南的目的就是要解決這些問題，提供使用者各種建議和技巧，讓和ChatGPT的對話變得更加容易和流暢。
	</p>
	<h2 class="u-text-7">咒文書</h2>
	{#each data as { act, prompt, firstPrompt }}
		<div class="u-flex u-items-center u-gap-1">
			<h3 class="u-text-6 u-my-0">{act}</h3>
			<button
				class="u-my-0 u-h-5.5 u-border-0 u-bg-transparent"
				on:click={() => {
					copyToClipboard(prompt, firstPrompt);
				}}
			>
				<IconClipboard />
			</button>
		</div>
		<p class="u-my-3 u-text-4.5">{prompt}</p>
		<div class="u-flex">
			<p class="u-my-3 u-text-4.5">我的第一個指令是：</p>
			<p class="u-my-3 u-text-4.5" contenteditable="true" bind:innerText={firstPrompt} />
			<div class="u-my-2 u-h-5">
				<IconPen />
			</div>
		</div>
	{/each}
	<div class="u-h-20" />
</div>

<style>
	* {
		font-family: 'Noto Serif TC', serif;
	}
</style>
