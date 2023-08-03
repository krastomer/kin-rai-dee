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
</script>

<button
	class="fixed flex flex-col space-y-4 items-center justify-center h-screen w-screen cursor-auto"
	on:click={setNewMenu}
>
	<h1 class="text-xl">{menu || 'กินไรดี'}</h1>
	<p class="text-stone-500">กดคลิ๊กซ้ายหรือ space bar เพื่อสุ่มเมนูใหม่</p>
</button>

<Header />
<Footer />
