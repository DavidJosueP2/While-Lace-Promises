<section id="hero" class="hero">
	<video class="hero-video" autoplay muted loop playsinline>
		<source src="/videos/video_banner.mp4" type="video/mp4" />
	</video>
	<div class="hero-overlay"></div>
	<div class="hero-watermark">PROMISES</div>
	<div class="hero-inner">
		<div class="hero-content">
			<div class="hero-brand fade-up">
				<img src="/imgs/logo-removebg.png" alt="White Lace & Promises" />
			</div>
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
	</div>
</section>

<style>
	.hero {
		position: relative;
		width: 100%;
		height: 96vh;
		min-height: 600px;
		overflow: hidden;
	}
	.hero-video {
		position: absolute;
		inset: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
		filter: grayscale(100%) brightness(0.86) contrast(0.96);
	}
	.hero-overlay {
		position: absolute;
		inset: 0;
		background:
			linear-gradient(to bottom, rgba(10, 10, 10, 0.5) 0%, rgba(10, 10, 10, 0.24) 42%, rgba(10, 10, 10, 0.64) 100%),
			radial-gradient(circle at center, rgba(10, 10, 10, 0.08) 0%, rgba(10, 10, 10, 0.52) 74%);
	}
	.hero-watermark {
		position: absolute;
		left: 50%;
		bottom: 5vh;
		z-index: 1;
		font-family: var(--font-heading);
		font-size: clamp(5rem, 13vw, 12rem);
		font-weight: 300;
		line-height: 0.8;
		letter-spacing: 0.04em;
		color: rgba(245, 245, 240, 0.072);
		transform: translateX(-50%);
		pointer-events: none;
		white-space: nowrap;
	}
	.hero-inner {
		position: relative;
		z-index: 2;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
		max-width: 1400px;
		margin: 0 auto;
		padding: 132px 48px 58px;
	}
	.hero-content {
		max-width: 760px;
		text-align: center;
	}
	.hero-brand {
		width: 96px;
		height: 54px;
		display: flex;
		align-items: center;
		justify-content: center;
		margin: 0 auto 22px;
		opacity: 1;
		pointer-events: none;
	}
	.hero-brand img {
		width: 100%;
		height: 100%;
		object-fit: contain;
		filter: invert(1) grayscale(1) brightness(1.35) contrast(1.18)
			drop-shadow(0 10px 26px rgba(0, 0, 0, 0.54));
	}
	.hero-kicker {
		font-family: var(--font-body);
		font-size: 0.64rem;
		font-weight: 500;
		letter-spacing: 0.34em;
		color: var(--gold);
	}
	.hero-title {
		font-family: var(--font-heading);
		font-size: clamp(3rem, 5.8vw, 5.45rem);
		font-weight: 300;
		line-height: 1.02;
		color: var(--off-white);
		margin-top: 16px;
	}
	.hero-title em {
		font-style: italic;
		color: var(--gold);
	}
	.hero-rule {
		width: min(24vw, 220px);
		height: 1px;
		margin: 24px auto 22px;
		background: linear-gradient(to right, transparent, var(--gold), transparent);
	}
	.hero-sub {
		font-family: var(--font-body);
		font-size: 0.8rem;
		font-weight: 300;
		line-height: 1.8;
		color: var(--light-grey);
		max-width: 590px;
		margin: 0 auto;
	}
	.hero-btns {
		display: flex;
		justify-content: center;
		gap: 16px;
		margin-top: 30px;
		flex-wrap: wrap;
	}
	.btn-gold,
	.btn-outline {
		font-family: var(--font-body);
		font-size: 0.65rem;
		font-weight: 500;
		letter-spacing: 0.2em;
		padding: 13px 30px;
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
			height: 94vh;
			min-height: 620px;
		}
		.hero-inner {
			padding: 112px 22px 42px;
		}
		.hero-watermark {
			bottom: 11vh;
			font-size: clamp(4.2rem, 20vw, 7rem);
		}
		.hero-title {
			font-size: clamp(2.7rem, 12vw, 4.2rem);
		}
		.hero-brand {
			width: 88px;
			height: 50px;
			margin-bottom: 18px;
		}
		.hero-rule {
			width: 72%;
			margin: 24px auto 22px;
		}
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
