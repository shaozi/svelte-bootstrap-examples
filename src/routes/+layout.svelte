<script lang="ts">
	import type { LayoutData } from './$types';
	import ThemeSwitch from './theme-switch.svelte';
	export let data: LayoutData;
	let routes = [
		{ href: '/', name: 'Home' },
		{ href: '/toasts', name: 'Toast' },
		{ href: '/tooltips', name: 'Tooltip' }
	];
</script>

<main class="d-flex flex-nowrap">
	<div
		class="d-flex flex-column flex-shrink-0 p-3 border-end bg-body-tertiary"
		style="height: 100vh; overflow-y: scroll;"
	>
		<div class="d-flex align-items-center justify-content-between">
			<strong><i class="bi-bootstrap-fill" /> Svelte+Bootstrap</strong>
		</div>
		<hr />
		<ul class="nav nav-pills flex-column mb-auto ps-3">
			{#each routes as route}
				<li class="nv-item">
					<a class="nav-link" class:active={data.pathname == route.href} href={route.href}>
						{route.name}
					</a>
				</li>
			{/each}
		</ul>
		<hr />
		<div class="d-flex align-items-center">
			<div class="text-secondary">Shaozi</div>
			<div class="ms-auto">
				<ThemeSwitch />
			</div>
		</div>
	</div>

	<div class="container-fluid p-5 m-0" style="height: 100vh; overflow-y: scroll; flex-grow: 1">
		<slot />
	</div>
</main>

<style>
	:global(body) {
		height: 100vh;
		overflow: hidden;
	}
</style>
