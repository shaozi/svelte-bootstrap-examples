<script lang="ts">
	import HighlightCode from './highlight-code.svelte';
	export let title: string;
	export let document: string;
	export let code: string;
</script>

<article>
	<h1>{title}</h1>
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
		<div class="list-group-item bg-body-tertiary text-secondary">CODE</div>
		<div class="list-group-item bg-body-tertiary p-0">
			<HighlightCode class="px-4" {code} />
		</div>
	</div>
</article>
