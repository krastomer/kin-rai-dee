<script lang="ts">
	import _ from 'lodash';
	const foods: string[] = ['pad kapao', 'khai jeaw moo sub', 'kaprao kung', 'pad thai', 'hoy tod'];

	let menu: string;

	function setNewMenu() {
		let newMenu: string;
		let count: number = 0;
		do {
			newMenu = _.sample(foods) || '';
			count++;
		} while (_.isEqual(newMenu, menu) && count < 5);
		menu = newMenu;
	}

	setNewMenu();
</script>

<h1>{menu}</h1>
<button on:click={setNewMenu}>new menu</button>
