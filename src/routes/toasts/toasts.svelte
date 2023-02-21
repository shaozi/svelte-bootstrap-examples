<script lang="ts">
	let toastElement: HTMLElement
</script>

<button
	class="btn btn-primary"
	on:click={async () => {
		const { Toast } = await import('bootstrap')
		let toast = Toast.getOrCreateInstance(toastElement)
		toast.show()
	}}
>
	Show Toast
</button>
<button class="btn btn-warning" data-bs-dismiss="toast" data-bs-target="#my-toast"
	>Hide Toast</button
>
<div class="bg-dark p-5 align-items-center">
	<div
		id="my-toast"
		class="toast"
		role="alert"
		aria-live="assertive"
		aria-atomic="true"
		on:hidden.bs.toast={() => {
			console.log('hidden')
		}}
		bind:this={toastElement}
	>
		<div class="toast-header">
			<strong class="me-auto">
				<i class="bi-info-circle-fill text-primary me-1" /> Bootstrap
			</strong>
			<small class="text-muted">11 mins ago</small>
			<button type="button" class="btn-close" data-bs-dismiss="toast" aria-label="Close" />
		</div>
		<div class="toast-body">Hello, world! This is a toast message.</div>
	</div>
</div>
