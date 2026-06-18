<script lang="ts">
	let { scrollY = 0 } = $props();
	let mobileOpen = $state(false);
	let solid = $derived(scrollY > 80);

	function toggle() {
		mobileOpen = !mobileOpen;
		document.body.style.overflow = mobileOpen ? 'hidden' : '';
	}
	function close() {
		mobileOpen = false;
		document.body.style.overflow = '';
	}
</script>

<nav class="nav" class:solid>
	<div class="nav-inner">
		<div class="nav-left">
			<a href="/about" class="nav-link">ABOUT</a>
			<a href="/events" class="nav-link">EVENTS</a>
		</div>
		<a href="/" class="nav-logo" aria-label="White Lace & Promises home">
			<img src="/imgs/logo-removebg.png" alt="" aria-hidden="true" />
			<span>WHITE LACE & PROMISES</span>
		</a>
		<div class="nav-right">
			<a href="/gallery" class="nav-link">GALLERY</a>
			<a href="/enquiry" class="nav-enquire">ENQUIRE</a>
		</div>
		<button class="hamburger" onclick={toggle} aria-label="Menu">
			<span class="bar" class:open={mobileOpen}></span>
			<span class="bar" class:open={mobileOpen}></span>
			<span class="bar" class:open={mobileOpen}></span>
		</button>
	</div>
</nav>

{#if mobileOpen}
	<div class="mobile-overlay" role="dialog">
		<div class="mobile-menu">
			<a href="/about" class="mobile-link" onclick={close}>ABOUT</a>
			<a href="/events" class="mobile-link" onclick={close}>EVENTS</a>
			<a href="/gallery" class="mobile-link" onclick={close}>GALLERY</a>
			<a href="/#customers" class="mobile-link" onclick={close}>COUPLES</a>
			<a href="/#contact" class="mobile-link" onclick={close}>CONTACT</a>
			<a href="/enquiry" class="mobile-enquire" onclick={close}>ENQUIRE</a>
		</div>
	</div>
{/if}

<style>
	.nav {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		z-index: 100;
		padding: 20px 48px;
		transition:
			background 0.4s ease,
			padding 0.4s ease,
			backdrop-filter 0.4s ease;
	}
	.nav.solid {
		background: rgba(10, 10, 10, 0.95);
		backdrop-filter: blur(12px);
		padding: 14px 48px;
	}
	.nav-inner {
		display: flex;
		align-items: center;
		justify-content: space-between;
		max-width: 1400px;
		margin: 0 auto;
	}
	.nav-left,
	.nav-right {
		display: flex;
		align-items: center;
		gap: 32px;
		flex: 1;
	}
	.nav-right {
		justify-content: flex-end;
	}
	.nav-link {
		font-family: var(--font-body);
		font-size: 0.7rem;
		font-weight: 400;
		letter-spacing: 0.25em;
		color: var(--off-white);
		transition: color 0.3s;
	}
	.nav-link:hover {
		color: var(--gold);
	}
	.nav-logo {
		position: relative;
		display: flex;
		align-items: center;
		justify-content: center;
		min-width: 250px;
		font-family: var(--font-body);
		font-size: 0.75rem;
		font-weight: 400;
		letter-spacing: 0.35em;
		color: var(--gold);
		white-space: nowrap;
		text-align: center;
		transition: color 0.3s ease;
	}
	.nav-logo:hover {
		color: var(--gold-hover);
	}
	.nav-logo span {
		position: relative;
		z-index: 2;
	}
	.nav-logo img {
		position: absolute;
		left: 50%;
		top: 50%;
		z-index: 1;
		width: 92px;
		height: 46px;
		object-fit: contain;
		opacity: 0.18;
		filter: invert(1) grayscale(1);
		transform: translate(-50%, -50%);
		pointer-events: none;
	}
	.nav-enquire {
		font-family: var(--font-body);
		font-size: 0.65rem;
		font-weight: 500;
		letter-spacing: 0.2em;
		color: var(--gold);
		border: 1px solid var(--gold);
		padding: 10px 24px;
		transition:
			background 0.3s,
			color 0.3s;
	}
	.nav-enquire:hover {
		background: var(--gold);
		color: var(--black);
	}
	.hamburger {
		display: none;
		flex-direction: column;
		gap: 5px;
		background: none;
		border: none;
		cursor: pointer;
		padding: 4px;
	}
	.bar {
		width: 24px;
		height: 1.5px;
		background: var(--off-white);
		transition:
			transform 0.3s,
			opacity 0.3s;
	}
	.bar.open:nth-child(1) {
		transform: rotate(45deg) translate(4px, 5px);
	}
	.bar.open:nth-child(2) {
		opacity: 0;
	}
	.bar.open:nth-child(3) {
		transform: rotate(-45deg) translate(4px, -5px);
	}

	.mobile-overlay {
		position: fixed;
		inset: 0;
		z-index: 99;
		background: rgba(10, 10, 10, 0.98);
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.mobile-menu {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 28px;
	}
	.mobile-link {
		font-family: var(--font-body);
		font-size: 0.8rem;
		letter-spacing: 0.3em;
		color: var(--off-white);
		transition: color 0.3s;
	}
	.mobile-link:hover {
		color: var(--gold);
	}
	.mobile-enquire {
		font-family: var(--font-body);
		font-size: 0.7rem;
		letter-spacing: 0.2em;
		color: var(--gold);
		border: 1px solid var(--gold);
		padding: 12px 32px;
		margin-top: 12px;
		transition:
			background 0.3s,
			color 0.3s;
	}
	.mobile-enquire:hover {
		background: var(--gold);
		color: var(--black);
	}

	@media (max-width: 768px) {
		.nav {
			padding: 16px 20px;
		}
		.nav.solid {
			padding: 12px 20px;
		}
		.nav-left,
		.nav-right {
			display: none;
		}
		.hamburger {
			display: flex;
		}
		.nav-logo {
			min-width: auto;
			font-size: 0.6rem;
			letter-spacing: 0.25em;
		}
		.nav-logo img {
			width: 72px;
			height: 36px;
		}
	}
</style>
