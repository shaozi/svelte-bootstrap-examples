<script lang="ts">
	import hljs from 'highlight.js';
	import { onMount } from 'svelte';
	export let title: string;
	export let document: string;
	export let code: string;
	onMount(() => {
		hljs.highlightAll();
	});
</script>

<article class="my-4">
	<h3>{title}</h3>
	<div>
		<a href={`https://getbootstrap.com/docs/5.3/components/${document}`}>
			Bootstrap Document <i class="bi-box-arrow-up-right ms-2" />
		</a>
	</div>
	<div class="mt-3">
		<slot name="description" />
	</div>
	<div class="list-group mt-4">
		<div class="list-group-item bg-body-tertiary text-secondary">EXAMPLE</div>
		<div class="list-group-item p-4">
			<slot name="example" />
		</div>
		<div class="list-group-item bg-body-tertiary p-0">
			<pre><code class="p-3 m-0">{code}</code></pre>
		</div>
	</div>
</article>
