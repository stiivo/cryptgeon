<script context="module">
	import { browser, dev } from '$app/env'
	export const hydrate = dev
	export const router = browser
	export const prerender = true
</script>

<svelte:head>
	<title>About</title>
</svelte:head>

<section class="content">
	<h1>About</h1>

	<p>
		<i>cryptgeon</i> is a secure, open source sharing note service inspired by
		<a href="https://privnote.com"><i>PrivNote</i></a>.
	</p>

	<p>
		<b>▶ how does it work?</b>
		<br />
		each note has a 512bit generated <i>id</i> that is used to retrieve the note. the note is then encrypted
		with aes in gcm mode on the client side and then sent to the server. data is stored in memory and
		never persisted to disk. the server never sees the encryption key and cannot decrypt the contents
		of the notes even if it tried to.
	</p>

	<b>▶ features</b>
	<ul>
		<li>server cannot decrypt contents due to client side encryption</li>
		<li>view and time constraints</li>
		<li>in memory, no persistence</li>
	</ul>

	<p>
		<b>▶ tech stack</b>
		<br />
		the backend is written in rust and the frontend is svelte and typescript.
		<br />
		you are welcomed to check & audit the
		<a href="https://github.com/cupcakearmy/cryptgeon" target="_blank" rel="noopener">source code</a
		>.
	</p>

	<p>
		<br />
		<b>▶ attributions</b>
		<br />
		<small>
			icons made by <a href="https://www.freepik.com" title="Freepik">freepik</a> from
			<a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a>
		</small>
	</p>
</section>

<style>
	section {
		width: 100%;
	}

	ul {
		margin: 0;
		padding: 0;
		padding-left: 1rem;
		list-style: square;
	}
</style>
