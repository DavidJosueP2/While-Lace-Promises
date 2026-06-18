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
		filter: grayscale(100%) brightness(0.78) contrast(1.02);
	}
	.hero-overlay {
		position: absolute;
		inset: 0;
		background:
			linear-gradient(to right, rgba(10, 10, 10, 0.78) 0%, rgba(10, 10, 10, 0.42) 42%, rgba(10, 10, 10, 0.14) 100%),
			linear-gradient(to top, rgba(10, 10, 10, 0.78) 0%, rgba(10, 10, 10, 0.14) 50%, rgba(10, 10, 10, 0.25) 100%);
	}
	.hero-watermark {
		position: absolute;
		right: -0.12em;
		bottom: 5vh;
		z-index: 1;
		font-family: var(--font-heading);
		font-size: clamp(5rem, 14vw, 13rem);
		font-weight: 300;
		line-height: 0.8;
		letter-spacing: 0.04em;
		color: rgba(245, 245, 240, 0.028);
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
		padding: 140px 64px 44px;
	}
	.hero-content {
		max-width: 650px;
	}
	.hero-brand {
		width: 112px;
		height: 64px;
		display: flex;
		align-items: center;
		justify-content: center;
		margin-bottom: 18px;
		opacity: 0.82;
		pointer-events: none;
	}
	.hero-brand img {
		width: 100%;
		height: 100%;
		object-fit: contain;
		filter: invert(1) grayscale(1) contrast(1.08) drop-shadow(0 10px 28px rgba(0, 0, 0, 0.42));
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
		font-size: clamp(3rem, 5.3vw, 4.85rem);
		font-weight: 300;
		line-height: 1.04;
		color: var(--off-white);
		margin-top: 16px;
	}
	.hero-title em {
		font-style: italic;
		color: var(--gold);
	}
	.hero-rule {
		width: min(34vw, 300px);
		height: 1px;
		margin: 20px 0 20px;
		background: linear-gradient(to right, var(--gold), rgba(201, 163, 71, 0.1), transparent);
	}
	.hero-sub {
		font-family: var(--font-body);
		font-size: 0.8rem;
		font-weight: 300;
		line-height: 1.8;
		color: var(--light-grey);
		max-width: 560px;
	}
	.hero-btns {
		display: flex;
		gap: 16px;
		margin-top: 24px;
		flex-wrap: wrap;
	}
	.hero-details {
		display: flex;
		align-items: center;
		gap: 18px;
		margin-top: 34px;
		padding-top: 16px;
		border-top: 1px solid rgba(245, 245, 240, 0.1);
		font-family: var(--font-body);
		font-size: 0.62rem;
		font-weight: 500;
		letter-spacing: 0.24em;
		text-transform: uppercase;
		color: rgba(245, 245, 240, 0.58);
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
			font-size: clamp(2.75rem, 12vw, 4rem);
		}
		.hero-brand {
			width: 96px;
			height: 56px;
			margin-bottom: 14px;
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
