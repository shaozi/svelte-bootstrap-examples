<script lang="ts">
	import { Popover } from 'bootstrap';
	import { onMount } from 'svelte';

	function initPopovers(): Popover[] {
		let nodes = document.querySelectorAll('[data-bs-toggle="popover"]');
		return [...nodes].map((popoverNode) => new Popover(popoverNode));
	}
	onMount(() => {
		initPopovers();
	});
</script>

<div>
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
