<script lang="ts">
	import '../app.css';
	import { page } from '$app/state';

	let { children } = $props();

	const nav = [
		{ href: '/', label: 'レシピ提案' },
	];
</script>

<div class="shell">
	<header>
		<a class="brand" href="/">🍁 旬の食材レシピ</a>
		<nav>
			{#each nav as item (item.href)}
				<a href={item.href} aria-current={page.url.pathname === item.href ? 'page' : undefined}>
					{item.label}
				</a>
			{/each}
		</nav>
	</header>

	<main>
		{@render children()}
	</main>

	<footer>SvelteKit + 旬の食材レシピ提案アプリ</footer>
</div>

<style>
	.shell {
		max-width: 44rem;
		margin: 0 auto;
		padding: 1.5rem 1rem 3rem;
		min-height: 100dvh;
		display: flex;
		flex-direction: column;
	}

	header {
		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 1rem;
		flex-wrap: wrap;
		padding-bottom: 1rem;
		border-bottom: 1px solid #fed7aa;
	}

	.brand {
		font-weight: 700;
		font-size: 1.1rem;
		text-decoration: none;
		color: #7c2d12;
	}

	nav {
		display: flex;
		gap: 0.5rem;
	}

	nav a {
		padding: 0.35rem 0.75rem;
		border-radius: 999px;
		text-decoration: none;
		color: #718096;
		font-size: 0.9rem;
		transition: background 0.2s, color 0.2s;
	}

	nav a:hover {
		color: #ea580c;
		background: #ffedd5;
	}

	nav a[aria-current='page'] {
		background: #ea580c;
		color: #fff;
	}

	main {
		flex: 1;
		padding-top: 1.5rem;
	}

	footer {
		padding-top: 2rem;
		font-size: 0.75rem;
		color: #a0aec0;
		text-align: center;
	}
</style>
