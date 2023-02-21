<script>
	import HighlightCode from '../lib/highlight-code.svelte'
</script>

<div>
	<div class="banner d-flex flex-column align-items-center p-5 text-light mb-5">
		<h1>How to use Bootstrap in SvelteKit</h1>
		<h1 class="d-flex align-items-center">
			<img class="mx-3" src="Svelte_Logo.svg" id="svelte-logo" height="120px" alt="svelte logo" />
			<img
				class="mx-3"
				src="Bootstrap_Logo.svg"
				id="bootstrap-logo"
				height="100px"
				alt="bootstrap logo"
			/>
		</h1>
	</div>

	<h2>Introduction</h2>
	<p>
		Bootstrap a powerful, feature-packed frontend toolkit. It defines and implements a complete
		suite of commonly used components. All the details about responsiveness and accessibility have
		been carefully considered and implemented under the hood. Its quality and easy to use make
		Bootstrap one of the most popular frontend toolkit.
	</p>
	<p>
		Bootstrap has css and JavaScript to control the look and behavior of the components. The
		JavaScript lib is designed for frontend only, that means it is expecting `document` and `window`
		objects to be there the moment you import it in your page.
	</p>
	<p>
		Because Svelte is compiled into HTML, css, and JavaScript. Svelte can make use of Bootstrap's
		CSS without any changes. However, SvelteKit with SSR will run the Javascript on the server too.
		Therefore, you have to put the `import` statement inside `onMount()` to make sure the Javascript
		will be run in browser:
	</p>
	<HighlightCode
		class="rounded border p-3"
		code={`
import { onMount } from 'svelte'
onMount(async ()=>{
	const { Toast } = await import('bootstrap')
})
	`}
	/>

	<h2>Installation</h2>
	<p>First, let's install the needed libraries:</p>
	<HighlightCode
		class="rounded border p-3"
		code={'npm install bootstrap\nnpm install @type/bootstrap\nnpm install @popper/core'}
	/>
</div>

<style>
	.banner {
		background: linear-gradient(95deg, #9013fe, #ff3f00);
		border-radius: 32px;
		overflow: hidden;
	}
</style>
