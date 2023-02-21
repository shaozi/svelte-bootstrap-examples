<script lang="ts">
	import hljs from 'highlight.js';
	import { onMount } from 'svelte';

	export let code: string;

	let html: string;
	onMount(() => {
		html = hljs.highlightAuto(code).value;
	});
</script>

{#if html}
	<pre class={$$restProps.class || ''}><code>{@html html}</code></pre>
{/if}
