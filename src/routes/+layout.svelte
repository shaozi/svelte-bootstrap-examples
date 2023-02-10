<script lang="ts">
	import { onMount } from 'svelte';

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
	import hljs from 'highlight.js';
	onMount(() => {});
	onMount(() => {
		savedTheme = getPreferredTheme();
		setTheme(savedTheme);
		window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', () => {
			if (savedTheme == 'auto') {
				setTheme(getPreferredTheme());
			}
		});
		console.log('onMount called');
	});
</script>

<nav class="navbar navbar-expand-lg bg-body-tertiary fixed-top border-bottom">
	<div class="container">
		<span class="navbar-brand"><i class="bi-bootstrap-fill" /> Svelte Bootstrap</span>
		<ul class="navbar-nav">
			<li class="nv-item">
				<a class="nav-link" href="/">Home</a>
			</li>
			<li class="nv-item">
				<a class="nav-link" href="/toasts">Toasts</a>
			</li>
			<li class="nv-item">
				<a class="nav-link" href="/tooltips">Tooltips</a>
			</li>
		</ul>

		<ul class="navbar-nav ms-auto">
			<li class="nav-item dropdown">
				<button
					class="nav-link border-0 bg-transparent dropdown-toggle"
					data-bs-toggle="dropdown"
					aria-expanded="false"
				>
					<i
						class:bi-sun-fill={savedTheme == 'light'}
						class:bi-moon-stars-fill={savedTheme == 'dark'}
						class:bi-circle-half={savedTheme == 'auto'}
					/>
				</button>
				<ul class="dropdown-menu p-1 dropdown-menu-end">
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
			</li>
		</ul>
	</div>
</nav>
<div style:margin-top={'5rem'} class="container">
	<slot />
</div>
