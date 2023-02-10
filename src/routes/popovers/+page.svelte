<script>
	import Article from '../article.svelte';
	import Popovers from './popovers.svelte';
	let code = `<script lang="ts">
	import { Popover } from 'bootstrap';
	import { onMount } from 'svelte';

	function initPopovers(): Popover[] {
		let nodes = document.querySelectorAll('[data-bs-toggle="popover"]');
		return [...nodes].map((popoverNode) => new Popover(popoverNode));
	}
	onMount(() => {
		initPopovers();
	});
<\/script>
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
`;
</script>

<Article title="Popovers" document="popovers" {code}>
	<div slot="description">
		Popover needs to be initialized by Bootstrap's JavaScript class <code>Popover</code>
	</div>
	<div slot="example">
		<Popovers />
	</div>
</Article>
