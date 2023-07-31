<script lang="ts">
	import _ from 'lodash';
	import { foods } from '../constants/food';
	import Footer from './footer.svelte';
	import Header from './header.svelte';

	let recentPick: string[] = [];

	let menu: string;

	function setNewMenu() {
		let newMenu: string;
		let count: number = 0;
		do {
			newMenu = _.sample(foods)?.name || '';
			count++;
		} while (_.isEqual(newMenu, menu) && count < 3);
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
</script>

<button
	class="fixed flex items-center justify-center h-screen w-screen cursor-auto"
	on:click={setNewMenu}
	on:keyup={onKeyDown}
>
	<p class="text-xl">{menu || 'กินไรดี'}</p>
</button>

<Header />
<Footer />
