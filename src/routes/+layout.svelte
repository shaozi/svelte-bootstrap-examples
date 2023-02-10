<script lang="ts">
	import type { LayoutData } from './$types';
	import ThemeSwitch from './theme-switch.svelte';
	export let data: LayoutData;
	let routes = [
		{ href: '/', name: 'Home' },
		{ href: '/toasts', name: 'Toast' },
		{ href: '/tooltips', name: 'Tooltip' },
		{ href: '/popovers', name: 'Popover' },
		{ href: '/scrollspy', name: 'Scrollspy' },
		{ href: '/all-in-one', name: 'All in One' }
	];
</script>

<main class="d-flex flex-nowrap">
	<div
		class="d-flex flex-column flex-shrink-0 p-3 border-end bg-body-tertiary"
		style="height: 100vh; overflow-y: scroll;"
	>
		<div class="d-flex align-items-center justify-content-between">
			<div class="h5">
				<img src="/Svelte_Logo.svg" alt="svelte logo" height="24px" />
				<span style="color: #FF3E00;"> Svelte</span>
				+
				<img src="/Bootstrap_Logo.svg" alt="bootstrap logo" height="24px" />
				<span style="color: #6610f2;"> Bootstrap</span>
			</div>
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
			<i class="bi-github" />
			<div class="ms-auto">
				<ThemeSwitch />
			</div>
		</div>
	</div>

	<div class="container-fluid px-5 m-0" style="height: 100vh; overflow-y: scroll; flex-grow: 1">
		<slot />
	</div>
</main>

<style>
	:global(body) {
		height: 100vh;
		overflow: hidden;
	}
</style>
