<section id="hero" class="hero">
	<video class="hero-video" autoplay muted loop playsinline>
		<source src="/videos/video_banner.mp4" type="video/mp4" />
	</video>
	<div class="hero-overlay"></div>
	<div class="hero-watermark">PROMISES</div>
	<div class="hero-inner">
		<div class="hero-content">
			<p class="hero-kicker fade-up">WEDDING & EVENT STYLING</p>
			<h1 class="hero-title fade-up delay-1">
				Designed with Grace,<br />Styled with <em>Heart</em>
			</h1>
			<div class="hero-rule fade-up delay-2"></div>
			<p class="hero-sub fade-up delay-2">
				Step into a world of elegance, charm, and unforgettable moments.<br />
				White Lace & Promises brings celebrations to life with styling, planning and detail-rich
				design.
			</p>
			<div class="hero-btns fade-up delay-3">
				<a href="/enquiry" class="btn-gold">BOOK YOUR EVENT</a>
				<a href="/gallery" class="btn-outline">VIEW GALLERY</a>
			</div>
		</div>
		<div class="hero-details fade-up delay-3" aria-label="White Lace and Promises services">
			<span>Weddings</span>
			<span>Event Styling</span>
			<span>Celebrations</span>
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
	}
	.hero-video {
		position: absolute;
		inset: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
		filter: grayscale(100%) brightness(0.68) contrast(1.08);
	}
	.hero-overlay {
		position: absolute;
		inset: 0;
		background:
			linear-gradient(to right, rgba(10, 10, 10, 0.9) 0%, rgba(10, 10, 10, 0.56) 42%, rgba(10, 10, 10, 0.18) 100%),
			linear-gradient(to top, rgba(10, 10, 10, 0.86) 0%, rgba(10, 10, 10, 0.18) 48%, rgba(10, 10, 10, 0.36) 100%);
	}
	.hero-watermark {
		position: absolute;
		right: -0.12em;
		bottom: 5vh;
		z-index: 1;
		font-family: var(--font-heading);
		font-size: clamp(6rem, 16vw, 15rem);
		font-weight: 300;
		line-height: 0.8;
		letter-spacing: 0.04em;
		color: rgba(245, 245, 240, 0.055);
		pointer-events: none;
		white-space: nowrap;
	}
	.hero-inner {
		position: relative;
		z-index: 2;
		display: flex;
		flex-direction: column;
		justify-content: flex-end;
		width: 100%;
		height: 100%;
		max-width: 1400px;
		margin: 0 auto;
		padding: 140px 64px 46px;
	}
	.hero-content {
		max-width: 700px;
	}
	.hero-kicker {
		font-family: var(--font-body);
		font-size: 0.68rem;
		font-weight: 500;
		letter-spacing: 0.34em;
		color: var(--gold);
	}
	.hero-title {
		font-family: var(--font-heading);
		font-size: clamp(3.25rem, 6.4vw, 5.8rem);
		font-weight: 300;
		line-height: 0.98;
		color: var(--off-white);
		margin-top: 18px;
	}
	.hero-title em {
		font-style: italic;
		color: var(--gold);
	}
	.hero-rule {
		width: min(40vw, 360px);
		height: 1px;
		margin: 24px 0 22px;
		background: linear-gradient(to right, var(--gold), rgba(201, 163, 71, 0.1), transparent);
	}
	.hero-sub {
		font-family: var(--font-body);
		font-size: 0.82rem;
		font-weight: 300;
		line-height: 1.8;
		color: var(--light-grey);
		max-width: 590px;
	}
	.hero-btns {
		display: flex;
		gap: 16px;
		margin-top: 28px;
		flex-wrap: wrap;
	}
	.hero-details {
		display: flex;
		align-items: center;
		gap: 18px;
		margin-top: 42px;
		padding-top: 18px;
		border-top: 1px solid rgba(245, 245, 240, 0.16);
		font-family: var(--font-body);
		font-size: 0.62rem;
		font-weight: 500;
		letter-spacing: 0.24em;
		text-transform: uppercase;
		color: rgba(245, 245, 240, 0.72);
	}
	.hero-details span + span {
		position: relative;
		padding-left: 18px;
	}
	.hero-details span + span::before {
		content: '';
		position: absolute;
		left: 0;
		top: 50%;
		width: 4px;
		height: 4px;
		background: var(--gold);
		transform: translateY(-50%) rotate(45deg);
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
		.hero {
			min-height: 680px;
		}
		.hero-inner {
			padding: 122px 22px 36px;
		}
		.hero-watermark {
			right: -0.25em;
			bottom: 18vh;
			font-size: clamp(5rem, 22vw, 8rem);
		}
		.hero-title {
			font-size: clamp(3rem, 13vw, 4.4rem);
		}
		.hero-rule {
			width: 82%;
			margin: 24px 0 22px;
		}
		.hero-sub br {
			display: none;
		}
		.hero-btns {
			flex-direction: column;
			align-items: flex-start;
		}
		.btn-gold,
		.btn-outline {
			width: 220px;
			text-align: center;
		}
		.hero-details {
			align-items: flex-start;
			flex-direction: column;
			gap: 10px;
			margin-top: 38px;
		}
		.hero-details span + span {
			padding-left: 0;
		}
		.hero-details span + span::before {
			display: none;
		}
	}
</style>
