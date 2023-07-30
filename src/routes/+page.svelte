<script lang="ts">
	import _ from 'lodash';
	import { foods } from './food';

	let recentRandomList: string[] = [];

	let menu: string;

	function setNewMenu() {
		let newMenu: string;
		let count: number = 0;
		do {
			newMenu = _.sample(foods) || '';
			count++;
		} while (_.isEqual(newMenu, menu) && count < 5);
		if (menu) {
			recentRandomList = [...recentRandomList, menu];
		}
		menu = newMenu;
		console.log(recentRandomList);
	}

	function resetRecentMenu() {
		recentRandomList = [];
	}

	setNewMenu();
</script>

<button on:click={setNewMenu}>new menu</button>
<button on:click={resetRecentMenu}>reset</button>
<h1>{menu}</h1>

<ul>
	{#each recentRandomList as f, i}
		<h2>{f} {i}</h2>
	{/each}
</ul>
