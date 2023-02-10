<script>
	import Article from '../article.svelte';
	import Scrollspys from './scrollspys.svelte';
	let code = `<script lang="ts">
	import { ScrollSpy } from 'bootstrap';
	import { onMount } from 'svelte';

	function initScrollSpy(): ScrollSpy | null {
		let node = document.querySelector('#scrollspy-area');
		if (node) {
			return new ScrollSpy(node, { target: '#navbar' });
		}
		return null;
	}

	onMount(() => {
		initScrollSpy();
	});
<\/script>

<nav id="navbar">
	<ul class="nav nav-pills">
		<li class="nav-item">
			<a class="nav-link active" href="#scrollspyHeading1">First</a>
		</li>
		<li class="nav-item">
			<a class="nav-link" href="#scrollspyHeading2">Second</a>
		</li>
		<li class="nav-item dropdown">
			<a
				class="nav-link dropdown-toggle"
				data-bs-toggle="dropdown"
				href="/"
				role="button"
				aria-expanded="false">Dropdown</a
			>
			<ul class="dropdown-menu">
				<li><a class="dropdown-item" href="#scrollspyHeading3">Third</a></li>
				<li><a class="dropdown-item" href="#scrollspyHeading4">Fourth</a></li>
				<li><hr class="dropdown-divider" /></li>
				<li><a class="dropdown-item" href="#scrollspyHeading5">Fifth</a></li>
			</ul>
		</li>
	</ul>
</nav>
<div
	id="scrollspy-area"
	data-bs-spy="scroll"
	data-bs-target="#navbar"
	data-bs-offset="0"
	style="height: 7rem; overflow: scroll"
>
	<h4 id="scrollspyHeading1">First heading</h4>
	
	<h4 id="scrollspyHeading2">Second heading</h4>
	
	<h4 id="scrollspyHeading3">Third heading</h4>
	
	<h4 id="scrollspyHeading4">Fourth heading</h4>
	
	<h4 id="scrollspyHeading5">Fifth heading</h4>
	
</div>
`;
</script>

<Article title="Scrollspy" document="scrollspy" {code}>
	<div slot="description">
		Scrollspy needs to be initialized by Bootstrap's JavaScript class <code>ScrollSpy</code>
	</div>
	<div slot="example">
		<Scrollspys />
	</div>
</Article>
