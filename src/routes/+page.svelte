<script lang="ts">
	import _ from 'lodash';
	import { foods } from './food';
	import { Button } from 'flowbite-svelte';

	let recentPick: string[] = [];

	let menu: string;

	function setNewMenu() {
		let newMenu: string;
		let count: number = 0;
		do {
			newMenu = _.sample(foods) || '';
			count++;
		} while (_.isEqual(newMenu, menu) && count < 5);
		if (menu) {
			recentPick = [...recentPick, menu];
		}
		menu = newMenu;
		console.log(recentPick);
	}

	function resetRecentMenu() {
		recentPick = [];
	}

	setNewMenu();
</script>

<section class="fixed h-screen w-screen text-center place-items-center">
	<h1>{menu}</h1>
	<div>
		<Button on:click={setNewMenu}>new menu</Button>
		<Button on:click={resetRecentMenu}>reset</Button>
	</div>
	<ul class="text-left">
		{#each recentPick as name, i}
			<h2>{i + 1}: {name}</h2>
		{/each}
	</ul>
</section>
