<script lang="ts">
	import Tooltips from './tootips.svelte'
	import Article from '$lib/article.svelte'
	let code = `
<script lang="ts">
	import { onMount } from 'svelte';
	onMount(() => {
		const { Tooltip } = await import('bootstrap');
		const tooltipTriggerList = document.querySelectorAll('[data-bs-toggle="tooltip"]');
		let tips = [...tooltipTriggerList].map((tooltipTriggerEl) =>
			Tooltip.getOrCreateInstance(tooltipTriggerEl)
		);
	});
<\/script>

<button
    type="button"
    class="btn btn-secondary"
    data-bs-toggle="tooltip"
    data-bs-placement="top"
    title="Tooltip on top">
    Tooltip on top
</button>`
</script>

<Article title="Tooltips" document="tooltips" {code}>
	<div slot="description">
		Tooltip needs Bootstrap's JavaScript to initialize. Therefore, you need to import class <code
			>Tooltip</code
		>
		from bootstrap, and use <code>Tooltip</code> to initialize the HTML elements that need tooltips
		in the document in svelte's
		<code>onMount</code> function.
	</div>
	<div slot="example">
		<Tooltips />
	</div>
</Article>
