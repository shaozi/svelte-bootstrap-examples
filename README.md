# Svelte Bootstrap

1. install libraries

```sh
npm install bootstrap@5.3.0-alpha1
npm install @types/bootstrap
npm i @popperjs/core
```

2. Add bootstrap css to app.html head:

```html
<link
	href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css"
	rel="stylesheet"
	integrity="sha384-GLhlTQ8iRABdZLl6O3oVMWSktQOp6b7In1Zl3/Jr59b6EGGoI1aFkw7cmDA6j6gD"
	crossorigin="anonymous"
/>
```

3. import bootstrap in the svelte file:

```html
<script type="module">
	import * as bootstrap from 'bootstrap';
</script>
```
