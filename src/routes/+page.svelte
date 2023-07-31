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
			newMenu = _.sample(foods)?.name || '';
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

<div class="fixed flex flex-col h-screen w-screen items-center justify-center">
	<p class="text-9xl">{menu}</p>
	<div class="mt-10">
		<Button color="alternative" on:click={setNewMenu}>new menu</Button>
		<Button on:click={resetRecentMenu}>reset</Button>
	</div>
</div>

<div class="absolute bottom-0 left-0 w-screen">
	<footer class="bg-white rounded-lg shadow m-4 dark:bg-gray-800 relative">
		<div class="w-full mx-auto max-w-screen-xl p-4 md:flex md:items-center md:justify-between">
			<span class="text-sm text-gray-500 sm:text-center dark:text-gray-400"
				>© 2023 <a href="https://flowbite.com/" class="hover:underline">Flowbite™</a>. All Rights
				Reserved.
			</span>
			<ul
				class="flex flex-wrap items-center mt-3 text-sm font-medium text-gray-500 dark:text-gray-400 sm:mt-0"
			>
				<li>
					<a href="#" class="mr-4 hover:underline md:mr-6">About</a>
				</li>
				<li>
					<a href="#" class="mr-4 hover:underline md:mr-6">Privacy Policy</a>
				</li>
				<li>
					<a href="#" class="mr-4 hover:underline md:mr-6">Licensing</a>
				</li>
				<li>
					<a href="#" class="hover:underline">Contact</a>
				</li>
			</ul>
		</div>
	</footer>
</div>
