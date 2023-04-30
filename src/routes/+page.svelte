<script lang="ts">
	import Icon from '@iconify/svelte';
	import githubIcon from '@iconify/icons-mdi/github';
	import promptRawData from '../data/prompts.json';
	import homeIntro from '../data/home_intro.json';
	import IconClipboard from '$lib/components/svg/IconClipboard.svelte';
	var data = promptRawData;
	function copyToClipboard(i: number) {
		navigator.clipboard.writeText(data[i].prompt + '\n\n我的第一個指令是：' + data[i].firstPrompt);
	}
</script>

<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="true" />
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+TC&display=swap" rel="stylesheet" />

<div class="u-mx-1 md:u-mx-10 lg:u-mx-20 xl:u-mx80">
	<h1 class="u-text-8">ChatGPT 咒文指南</h1>
	<p class="u-text-4.5">
		{homeIntro.intro}
	</p>
	<h2>鳴謝</h2>
	<p class="u-text-4.5">
		大部分內容參考自 <a href="https://prompts.chat/" target="_blank">Awesome ChatGPT Prompts</a>
	</p>
	<h2>使用說明</h2>
	<p class="u-text-4.5">
		{homeIntro.how_to_use}
	</p>
	<div>
		<p class="u-text-4.5">
			{homeIntro.how_to_use_2}
		</p>
		<a class="u-text-black" href="https://github.com/TonyPepeBear/gpt-prompt" target="_blank">
			<Icon icon={githubIcon} width="64" height="64" />
		</a>
	</div>
	<h2 class="u-text-7">咒文書</h2>
	{#each data as { act, prompt, firstPrompt }, i}
		<div class="u-p-2 u-mb-4 u-border-solid u-border-1 u-border-black u-rounded-xl">
			<div class="u-flex u-items-center u-gap-1">
				<h3 class="u-text-6 u-my-0">{act}</h3>
				<button
					class="u-my-0 u-h-5.5 u-border-0 u-bg-transparent u-cursor-pointer"
					on:click={() => {
						copyToClipboard(i);
					}}
				>
					<IconClipboard />
				</button>
			</div>
			<p class="u-my-3 u-text-4.5">{prompt}</p>
			<div class="u-flex u-flex-col">
				<div class="u-flex">
					<p class="u-my-3 u-text-4.5">我的第一個指令是：✍⬇️</p>
				</div>
				<p
					class="u-my-3 u-text-4.5 u-text-gray-600 u-underline"
					contenteditable="true"
					bind:innerText={firstPrompt}
				/>
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
