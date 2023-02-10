<script lang="ts">
	import { Toast } from 'bootstrap';
	import Article from './article.svelte';
	let toastElement: HTMLElement;
	let code = `
<script lang="ts">
	import { Toast } from 'bootstrap';
	let toastElement: HTMLElement;
<\/script>

<button
    class="btn btn-primary"
    on:click={() => {
        let toast = Toast.getOrCreateInstance(toastElement);
        toast.show();
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
            console.log('hidden');
        }}
        bind:this={toastElement}
    >
        <div class="toast-header">
            <svg
                class="bd-placeholder-img rounded me-2"
                width="20"
                height="20"
                xmlns="http://www.w3.org/2000/svg"
                aria-hidden="true"
                preserveAspectRatio="xMidYMid slice"
                focusable="false"><rect width="100%" height="100%" fill="#007aff" /></svg
            >

            <strong class="me-auto">Bootstrap</strong>
            <small class="text-muted">11 mins ago</small>
            <button type="button" class="btn-close" data-bs-dismiss="toast" aria-label="Close" />
        </div>
        <div class="toast-body">Hello, world! This is a toast message.</div>
    </div>
</div>
`;
</script>

<Article title="Toasts" document="toasts" {code}>
	<div slot="description">
		<h4>Static Toasts</h4>
		<p>
			Static toasts are html elements that are pre-written in the page. All you need to do is to
			initialize the HTML element with Bootstrap's Javascript class
			<code>Toast</code>, then you can use <code>.show()</code> and <code>.hide()</code>
			to show and hide a toast.
		</p>
		<p>
			When use svelte's <code>on:[bs-...]</code> event handler in the toast element, for example
			<code>on:hidden.bs.toast</code>, vscode always shows an error saying the event is not
			assignable to the <code>div</code> element. That is because the event is not defined.
		</p>
		<p>
			To define that, you need to add an entry in <code>app.d.ts</code> file:
		</p>
		<pre><code
				>{`namespace svelteHTML {
    interface HTMLAttributes<T> {
        'on:hidden.bs.toast'?: () => void;
    }
}`}</code
			></pre>
	</div>
	<div slot="example">
		<button
			class="btn btn-primary"
			on:click={() => {
				let toast = Toast.getOrCreateInstance(toastElement);
				toast.show();
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
					console.log('hidden');
				}}
				bind:this={toastElement}
			>
				<div class="toast-header">
					<svg
						class="bd-placeholder-img rounded me-2"
						width="20"
						height="20"
						xmlns="http://www.w3.org/2000/svg"
						aria-hidden="true"
						preserveAspectRatio="xMidYMid slice"
						focusable="false"><rect width="100%" height="100%" fill="#007aff" /></svg
					>

					<strong class="me-auto">Bootstrap</strong>
					<small class="text-muted">11 mins ago</small>
					<button type="button" class="btn-close" data-bs-dismiss="toast" aria-label="Close" />
				</div>
				<div class="toast-body">Hello, world! This is a toast message.</div>
			</div>
		</div>
	</div>
</Article>
