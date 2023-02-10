<script lang="ts">
	import { Tooltip } from 'bootstrap';
	import { onMount } from 'svelte';
	import Article from '../article.svelte';
	function initTooltips(): Tooltip[] {
		const tooltipTriggerList = document.querySelectorAll('[data-bs-toggle="tooltip"]');
		return [...tooltipTriggerList].map((tooltipTriggerEl) =>
			Tooltip.getOrCreateInstance(tooltipTriggerEl)
		);
	}
	onMount(() => {
		let tips = initTooltips();
		console.log('tooltip onMount called');
	});

	let code = `
<script lang="ts">
	import { Tooltip } from 'bootstrap';
	import { onMount } from 'svelte';
	function initTooltips(): Tooltip[] {
		const tooltipTriggerList = document.querySelectorAll('[data-bs-toggle="tooltip"]');
		return [...tooltipTriggerList].map((tooltipTriggerEl) =>
			Tooltip.getOrCreateInstance(tooltipTriggerEl)
		);
	}
	onMount(() => {
		initTooltips();
	});
<\/script>

<button
    type="button"
    class="btn btn-secondary"
    data-bs-toggle="tooltip"
    data-bs-placement="top"
    title="Tooltip on top">
    Tooltip on top
</button>`;
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
		<button
			type="button"
			class="btn btn-secondary"
			data-bs-toggle="tooltip"
			data-bs-placement="top"
			title="Tooltip on top">Tooltip on top</button
		>
		<button
			type="button"
			class="btn btn-secondary"
			data-bs-toggle="tooltip"
			data-bs-placement="right"
			title="Tooltip on end">Tooltip on end</button
		>
		<button
			type="button"
			class="btn btn-secondary"
			data-bs-toggle="tooltip"
			data-bs-placement="bottom"
			title="Tooltip on bottom">Tooltip on bottom</button
		>
		<button
			type="button"
			class="btn btn-secondary"
			data-bs-toggle="tooltip"
			data-bs-placement="left"
			title="Tooltip on start">Tooltip on start</button
		>
		<button
			type="button"
			class="btn btn-secondary"
			data-bs-toggle="tooltip"
			data-bs-html="true"
			title="<em>Tooltip</em> <u>with</u> <b>HTML</b>">Tooltip with HTML</button
		>
	</div>
</Article>
