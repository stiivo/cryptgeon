<script lang="ts">
	import { getRandomBytes, Hex } from '$lib/crypto'

	import copyToClipboard from 'copy-to-clipboard'

	import Icon from './Icon.svelte'

	export let label: string = ''
	export let value

	export let copy: boolean = false
	export let random: boolean = false

	const initialType = $$restProps.type
	const isPassword = initialType === 'password'
	let hidden = true

	$: if (isPassword) {
		value
		$$restProps.type = hidden ? initialType : 'text'
	}

	function toggle() {
		hidden = !hidden
	}
	function copyFN() {
		copyToClipboard(value)
	}
	function randomFN() {
		value = Hex.encode(getRandomBytes(20))
	}
</script>

<label>
	<small disabled={$$restProps.disabled}>
		{label}
	</small>
	<input bind:value {...$$restProps} />
	<div class="icons">
		{#if isPassword}
			<Icon class="icon" icon={hidden ? 'eye-sharp' : 'eye-off-sharp'} on:click={toggle} />
		{/if}
		{#if random}
			<Icon class="icon" icon="dice-sharp" on:click={randomFN} />
		{/if}
		{#if copy}
			<Icon class="icon" icon="copy-sharp" on:click={copyFN} />
		{/if}
	</div>
</label>

<style>
	label {
		position: relative;
		display: block;
	}

	input {
		width: 100%;
		margin: 0;
		border: 2px solid var(--ui-bg-1);
		outline: none;
		padding: 0.5rem;
		height: 2.5rem;
	}
	input:hover,
	input:focus {
		border-color: var(--ui-clr-primary);
	}

	.icons {
		border: 1px red;
		position: absolute;
		right: 0.3rem;
		bottom: 0.3rem;
		display: flex;
		color: var(--ui-clr-primary);
	}
	.icons > :global(.icon) {
		width: 1.5rem;
		height: 1.5rem;
		background-color: var(--ui-bg-1);
		border: 2px solid var(--ui-bg-2);
		padding: 1px;
		cursor: pointer;
		margin-left: 0.25rem;
	}
	.icons > :global(.icon:hover) {
		border-color: var(--ui-clr-primary);
	}
</style>
