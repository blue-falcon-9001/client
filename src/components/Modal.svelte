<script>

	import { hideModal } from '../stores/modals'

	export let title = '';
	export let isActive;
	export let noHeader = false;

	if (isActive == undefined) isActive = true;

</script>

<style>

	.modal-container {
		position: fixed;
		top: 0;
		left: 0;
		overflow-x: hidden;
		overflow-y: auto;
		right: 0;
		bottom: 0;
		background-color: rgb(0,0,0,0.624);
		z-index: 100;
		padding: 0 var(--base-padding);
		outline: 0;
		display: none;
		align-items: center;
		justify-content: center;
	}
	.modal-container.active {
		display: flex;
	}

	.modal {
		width: 460px;
		border: 1px solid var(--jet-dim);
		border-radius: var(--base-radius);
		background-color: var(--eerie-black);
		overflow: hidden;
	}

	.modal-header {
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 0 var(--base-padding);
		height: 60px;
		background-color: var(--jet);
	}

	.modal-title {
		font-weight: 700;
	}

	.done-button {
		font-weight: 700;
		cursor: pointer;
		color: var(--green);
	}
	.done-button:hover {
		color: var(--green-dim);
	}

	.modal-body {
		overflow-y: scroll;
		max-height: 85vh;
	}

</style>

<div class:active={isActive} class='modal-container no-scrollbar'>

	<div class='modal' data-intercept="true">

		{#if !noHeader}
		<div class='modal-header'>
			<div class='modal-title'>{title}</div>
			<span class='done-button' on:click={hideModal}>Done</span>
		</div>
		{/if}

		<div class='modal-body no-scrollbar'>
			<slot></slot>
		</div>
		
	</div>

</div>