<script lang="ts">
	import { onMount } from 'svelte';
	// import { Dropdown } from 'bootstrap';
	const setTheme = function (theme: 'light' | 'dark' | 'auto') {
		if (theme === 'auto') {
			if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
				document.documentElement.setAttribute('data-bs-theme', 'dark');
				setHighlightTheme('dark');
			} else {
				document.documentElement.setAttribute('data-bs-theme', 'light');
				setHighlightTheme('light');
			}
		} else {
			document.documentElement.setAttribute('data-bs-theme', theme);
			setHighlightTheme(theme);
		}
		localStorage.setItem('theme', theme);
		savedTheme = theme;
	};

	let savedTheme: 'light' | 'dark' | 'auto';
	let dropdown: HTMLElement;
	function setHighlightTheme(theme: 'dark' | 'light') {
		let links = document.querySelectorAll('.hljs-theme');
		console.log(links);
		links.forEach((link) => {
			if (link.getAttribute('title') == theme) {
				link.removeAttribute('disabled');
			} else {
				link.setAttribute('disabled', 'disabled');
			}
		});
	}

	const getPreferredTheme = (): 'light' | 'dark' | 'auto' => {
		const storedTheme = localStorage.getItem('theme');
		if (storedTheme) {
			if (storedTheme != 'light' && storedTheme != 'dark' && storedTheme != 'auto') {
				return 'auto';
			}
			return storedTheme;
		}
		return window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light';
	};

	onMount(() => {
		savedTheme = getPreferredTheme();
		setTheme(savedTheme);
		window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', () => {
			if (savedTheme == 'auto') {
				setTheme(getPreferredTheme());
			}
		});
		const bootstrap = require('bootstrap');
		bootstrap.Dropdown.getOrCreateInstance(dropdown);
	});
</script>

<div>
	<button class="nav-link border-0 bg-transparent" data-bs-toggle="dropdown" aria-expanded="false">
		<i
			class:bi-sun={savedTheme == 'light'}
			class:bi-moon-stars-fill={savedTheme == 'dark'}
			class:bi-circle-half={savedTheme == 'auto'}
		/>
	</button>
	<ul class="dropdown-menu p-1 dropdown-menu-end" bind:this={dropdown}>
		<li>
			<button
				class="dropdown-item rounded-1"
				class:active={savedTheme == 'light'}
				on:click={() => {
					setTheme('light');
				}}><i class="bi-sun-fill me-2" /> Light</button
			>
		</li>
		<li>
			<button
				class="dropdown-item rounded-1 my-1"
				class:active={savedTheme == 'dark'}
				on:click={() => {
					setTheme('dark');
				}}><i class="bi-moon-stars-fill me-2" /> Dark</button
			>
		</li>
		<li>
			<button
				class="dropdown-item rounded-1"
				class:active={savedTheme == 'auto'}
				on:click={() => {
					setTheme('auto');
				}}><i class="bi-circle-half me-2" /> Auto</button
			>
		</li>
	</ul>
</div>
