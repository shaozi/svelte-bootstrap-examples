<script lang="ts">
	import { onMount } from 'svelte'
	let scrollspyArea: HTMLElement
	let navBar: HTMLElement
	onMount(async () => {
		const { ScrollSpy } = await import('bootstrap')

		ScrollSpy.getOrCreateInstance(scrollspyArea, { target: navBar })
	})
</script>

<nav bind:this={navBar} class="navbar">
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
	bind:this={scrollspyArea}
	data-bs-spy="scroll"
	data-bs-target="#navbar"
	data-bs-offset="0"
	class="border rounded p-3"
	style="height: 7rem; overflow: scroll"
>
	<h4 id="scrollspyHeading1">First heading</h4>
	<p>
		This is some placeholder content for the scrollspy page. Note that as you scroll down the page,
		the appropriate navigation link is highlighted. It's repeated throughout the component example.
		We keep adding some more example copy here to emphasize the scrolling and highlighting.
	</p>
	<h4 id="scrollspyHeading2">Second heading</h4>
	<p>
		This is some placeholder content for the scrollspy page. Note that as you scroll down the page,
		the appropriate navigation link is highlighted. It's repeated throughout the component example.
		We keep adding some more example copy here to emphasize the scrolling and highlighting.
	</p>
	<h4 id="scrollspyHeading3">Third heading</h4>
	<p>
		This is some placeholder content for the scrollspy page. Note that as you scroll down the page,
		the appropriate navigation link is highlighted. It's repeated throughout the component example.
		We keep adding some more example copy here to emphasize the scrolling and highlighting.
	</p>
	<h4 id="scrollspyHeading4">Fourth heading</h4>
	<p>
		This is some placeholder content for the scrollspy page. Note that as you scroll down the page,
		the appropriate navigation link is highlighted. It's repeated throughout the component example.
		We keep adding some more example copy here to emphasize the scrolling and highlighting.
	</p>
	<h4 id="scrollspyHeading5">Fifth heading</h4>
	<p>
		This is some placeholder content for the scrollspy page. Note that as you scroll down the page,
		the appropriate navigation link is highlighted. It's repeated throughout the component example.
		We keep adding some more example copy here to emphasize the scrolling and highlighting.
	</p>
</div>
