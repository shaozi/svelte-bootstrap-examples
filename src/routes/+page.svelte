<script>
	import HighlightCode from './highlight-code.svelte';
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
		been carefully considered and implemented under the hood. It's high quality and easy to use make
		Bootstrap one of the most popular frontend toolkit.
	</p>
	<p>
		Most of Bootstrap's components are css only. Except a few of them needs JavaScript for their
		behaviors.
	</p>
	<p>They are:</p>
	<ul>
		<li>Tooltips,</li>
		<li>Toasters,</li>
		<li>Popovers, and</li>
		<li>Scrollspy.</li>
	</ul>
	<p>
		Bootstrap comes with its own Javascript. However, with Svelte, we want to integrate them into
		Svelte.
	</p>
	<p>
		Because Svelte is compiled into HTML, css, and JavaScript. It is pretty easy to integrate 3rd
		party JavaScript into a Svelte project. The methods introduced in this article can also be used
		to integrate other JavaScript libraries into a Svelte project.
	</p>

	<h2>Installation</h2>
	<p>First, let's install the needed libraries:</p>
	<HighlightCode
		class="rounded border"
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
