<script lang="ts">
	import { Button, Modal, Input, ButtonGroup } from 'flowbite-svelte';

	let clickOutsideModal: boolean = true;
	let inputField: string;
</script>

<header class="top-0 fixed flex w-screen p-4 flex-row-reverse">
	<Button outline on:click={() => (clickOutsideModal = true)}>เพิ่มเมนูสุ่ม</Button>
</header>

<Modal title="เพิ่มเมนูสุ่ม" bind:open={clickOutsideModal} outsideclose>
	<ButtonGroup divClass="w-full flex flex-row">
		<Input value={inputField} />
		<Button outline color="dark">
			<svg
				xmlns="http://www.w3.org/2000/svg"
				fill="none"
				viewBox="0 0 24 24"
				stroke-width="1.5"
				stroke="currentColor"
				class="w-5 h-5 mr-2 text-blue-500 dark:text-blue-400"
				><path
					stroke-linecap="round"
					stroke-linejoin="round"
					d="M6 13.5V3.75m0 9.75a1.5 1.5 0 010 3m0-3a1.5 1.5 0 000 3m0 3.75V16.5m12-3V3.75m0 9.75a1.5 1.5 0 010 3m0-3a1.5 1.5 0 000 3m0 3.75V16.5m-6-9V3.75m0 3.75a1.5 1.5 0 010 3m0-3a1.5 1.5 0 000 3m0 9.75V10.5"
				/></svg
			>
			Settings
		</Button>
	</ButtonGroup>

	<svelte:fragment slot="footer">
		<Button on:click={() => {}}>เพิ่ม</Button>
		<Button color="alternative">ไม่เอาอะ ลบๆ</Button>
	</svelte:fragment>
</Modal>
