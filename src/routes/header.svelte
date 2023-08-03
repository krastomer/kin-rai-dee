<script lang="ts">
	import { Button, Modal, Input, ButtonGroup, Listgroup } from 'flowbite-svelte';

	let clickOutsideModal: boolean = false;
	// export let title;
	let inputField: string = '';

	let items: string[] = [];

	function addList() {
		console.log(inputField);
		items = [...items, inputField];
		console.log(items);
		inputField = '';
	}
</script>

<header class="top-0 fixed flex w-screen p-4 flex-row-reverse">
	<Button outline on:click={() => (clickOutsideModal = true)}>เพิ่มเมนูสุ่ม</Button>
</header>

<Modal title="เพิ่มเมนูสุ่ม" bind:open={clickOutsideModal} outsideclose>
	<ButtonGroup divClass="w-full flex flex-row">
		<Input
			bind:value={inputField}
			on:keypress={(e) => {
				if (e.code === 'Enter') {
					addList();
				}
			}}
		/>
		<Button color="primary" on:click={addList}>
			<svg
				class="w-6 h-6"
				aria-hidden="true"
				xmlns="http://www.w3.org/2000/svg"
				fill="currentColor"
				viewBox="0 0 20 20"
			>
				<path
					d="M9.546.5a9.5 9.5 0 1 0 9.5 9.5 9.51 9.51 0 0 0-9.5-9.5ZM13.788 11h-3.242v3.242a1 1 0 1 1-2 0V11H5.304a1 1 0 0 1 0-2h3.242V5.758a1 1 0 0 1 2 0V9h3.242a1 1 0 1 1 0 2Z"
				/>
			</svg>
		</Button>
	</ButtonGroup>

	{#if items.length > 0}
		<Listgroup {items} let:item class="w-full">
			{item}
		</Listgroup>
	{/if}

	<svelte:fragment slot="footer">
		<Button
			on:click={() => {
				clickOutsideModal = false;
			}}>เพิ่ม</Button
		>
		<Button color="alternative">ไม่เอาอะ ลบๆ</Button>
	</svelte:fragment>
</Modal>
