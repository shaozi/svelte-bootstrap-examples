<script lang="ts">
	import { onMount, onDestroy } from 'svelte'
	let popovers: any[] = []
	onMount(async () => {
		const { Popover } = await import('bootstrap')
		let nodes = document.querySelectorAll('[data-bs-toggle="popover"]')
		popovers = [...nodes].map((popoverNode) => Popover.getOrCreateInstance(popoverNode))
	})
	onDestroy(() => {
		popovers.forEach((pop) => {
			pop.hide()
		})
	})
</script>

<div>
	<div class="mb-3">
		<button
			type="button"
			class="btn btn-lg btn-danger"
			data-bs-toggle="popover"
			title="Popover title"
			data-bs-content="And here's some amazing content. It's very engaging. Right?"
			>Click to toggle popover</button
		>
	</div>

	<button
		type="button"
		class="btn btn-secondary"
		data-bs-container="body"
		data-bs-toggle="popover"
		data-bs-placement="top"
		data-bs-content="Vivamus sagittis lacus vel augue laoreet rutrum faucibus."
	>
		Popover on top
	</button>
	<button
		type="button"
		class="btn btn-secondary"
		data-bs-container="body"
		data-bs-toggle="popover"
		data-bs-placement="right"
		data-bs-content="Vivamus sagittis lacus vel augue laoreet rutrum faucibus."
	>
		Popover on end
	</button>
	<button
		type="button"
		class="btn btn-secondary"
		data-bs-container="body"
		data-bs-toggle="popover"
		data-bs-placement="bottom"
		data-bs-content="Vivamus sagittis lacus vel augue laoreet rutrum faucibus."
	>
		Popover on bottom
	</button>
	<button
		type="button"
		class="btn btn-secondary"
		data-bs-container="body"
		data-bs-toggle="popover"
		data-bs-placement="left"
		data-bs-content="Vivamus sagittis lacus vel augue laoreet rutrum faucibus."
	>
		Popover on start
	</button>
</div>
