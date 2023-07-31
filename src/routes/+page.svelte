<script lang="ts">
	import _ from 'lodash';
	import { foods } from './food';
	import { Button, Kbd } from 'flowbite-svelte';
	import Footer from './footer.svelte';

	let recentPick: string[] = [];

	let menu: string;

	function setNewMenu() {
		let newMenu: string;
		let count: number = 0;
		do {
			newMenu = _.sample(foods)?.name || '';
			count++;
		} while (_.isEqual(newMenu, menu) && count < 5);
		if (menu) {
			recentPick = [...recentPick, menu];
		}
		menu = newMenu;
	}

	function resetRecentMenu() {
		recentPick = [];
	}

	function onKeyDown(e: KeyboardEvent) {
		if (e.code === 'Space') {
			setNewMenu();
		}
	}
	function onClickDown(e: MouseEvent) {
		if (e.button === 0) {
			setNewMenu();
		}
	}
</script>

<svelte:window on:keydown={onKeyDown} on:click={onClickDown} />

<div class="fixed flex flex-col h-screen w-screen items-center justify-center">
	<h1 class="text-xl">{menu || 'กินไรดี'}</h1>
	<p class="text-slate-500"><Kbd class="p-1.5">Space bar</Kbd> หรือ click อะแหละ</p>
</div>

<Footer />
