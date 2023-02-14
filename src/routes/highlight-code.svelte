<script lang="ts">
	import hljs from 'highlight.js';
	import { onMount } from 'svelte';

	export let code: string;

	let html: string;
	onMount(() => {
		hljs.highlightAll();
	});
</script>

<pre class={$$restProps.class || ''}><code class="p-4">{code}</code></pre>
