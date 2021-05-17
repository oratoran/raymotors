<script>
	import { page } from '$app/stores';
    import logo from '/images/ray-motors-svg.svg';
</script>

<header>
	<div class="logo">
		<a href="/">
			<img src="{logo}" alt="Ray Motors Classic Mercedes Benz Garage" class="h-28" />
		</a>
	</div>

	<nav>
        <a sveltekit:prefetch href="/" class:active={$page.path === '/'}>Home</a>
        <a sveltekit:prefetch href="/about" class:active={$page.path === '/about'}>About</a>
        <a sveltekit:prefetch href="/cars"  class:active={$page.path === '/cars'}>Cars</a>
    </nav>

	<div class="corner">
		<!-- TODO put something else here? github link? -->
	</div>
</header>

<style>
    .logo {
        @apply flex justify-center p-4
    }
    nav {
        @apply text-center
    }
</style>