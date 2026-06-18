<script lang="ts">
	import Ornament from '$lib/components/Ornament.svelte';
</script>

<section id="hero" class="hero">
	<video class="hero-video" autoplay muted loop playsinline>
		<source src="/videos/video_banner.mp4" type="video/mp4" />
	</video>
	<div class="hero-overlay"></div>
	<div class="hero-content">
		<p class="section-label fade-up">Australian Wedding & Event Styling</p>
		<h1 class="hero-title fade-up delay-1">
			Where <em>Dreams</em><br />Take Shape
		</h1>
		<Ornament />
		<p class="hero-sub fade-up delay-2">
			Step into a world of elegance, charm, and unforgettable moments.<br />
			White Lace & Promises brings Australian celebrations to life with styling, planning and detail-rich
			design.
		</p>
		<div class="hero-btns fade-up delay-3">
			<a href="/enquiry" class="btn-gold">BOOK YOUR EVENT</a>
			<a href="/gallery" class="btn-outline">VIEW GALLERY</a>
		</div>
	</div>
</section>

<style>
	.hero {
		position: relative;
		width: 100%;
		height: 100vh;
		min-height: 600px;
		overflow: hidden;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.hero-video {
		position: absolute;
		inset: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
		filter: grayscale(100%) brightness(0.55);
	}
	.hero-overlay {
		position: absolute;
		inset: 0;
		background: linear-gradient(
			to bottom,
			rgba(0, 0, 0, 0.35) 0%,
			rgba(0, 0, 0, 0.15) 40%,
			rgba(0, 0, 0, 0.55) 100%
		);
	}
	.hero-content {
		position: relative;
		z-index: 2;
		text-align: center;
		max-width: 800px;
		padding: 0 24px;
	}
	.hero-title {
		font-family: var(--font-heading);
		font-size: clamp(2.8rem, 7vw, 5.5rem);
		font-weight: 300;
		line-height: 1.1;
		color: var(--off-white);
		margin-top: 16px;
	}
	.hero-title em {
		font-style: italic;
		color: var(--gold);
	}
	.hero-sub {
		font-family: var(--font-body);
		font-size: 0.82rem;
		font-weight: 300;
		line-height: 1.8;
		color: var(--light-grey);
		max-width: 540px;
		margin: 0 auto;
	}
	.hero-btns {
		display: flex;
		gap: 16px;
		justify-content: center;
		margin-top: 32px;
		flex-wrap: wrap;
	}
	.btn-gold,
	.btn-outline {
		font-family: var(--font-body);
		font-size: 0.65rem;
		font-weight: 500;
		letter-spacing: 0.2em;
		padding: 14px 32px;
		transition: all 0.3s ease;
		cursor: pointer;
		text-decoration: none;
	}
	.btn-gold {
		background: var(--gold);
		color: var(--black);
		border: 1px solid var(--gold);
	}
	.btn-gold:hover {
		background: var(--gold-hover);
		border-color: var(--gold-hover);
	}
	.btn-outline {
		background: transparent;
		color: var(--off-white);
		border: 1px solid rgba(245, 245, 240, 0.4);
	}
	.btn-outline:hover {
		border-color: var(--gold);
		color: var(--gold);
	}

	@media (max-width: 768px) {
		.hero-sub br {
			display: none;
		}
		.hero-btns {
			flex-direction: column;
			align-items: center;
		}
		.btn-gold,
		.btn-outline {
			width: 220px;
			text-align: center;
		}
	}
</style>
