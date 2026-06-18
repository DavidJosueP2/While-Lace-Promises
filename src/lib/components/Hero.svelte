<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';
	import { ScrollTrigger } from 'gsap/ScrollTrigger';

	gsap.registerPlugin(ScrollTrigger);

	let heroEl: HTMLElement;
	let videoEl: HTMLVideoElement;

	onMount(() => {
		const entranceDone = sessionStorage.getItem('wlp_entered');
		const startDelay = entranceDone ? 0.2 : 0;

		// Wait for entrance to complete if it hasn't already
		const initAnimations = () => {
			const tl = gsap.timeline({ delay: startDelay });

			// Video clip-path reveal from center — faster
			tl.fromTo(videoEl,
				{ clipPath: 'inset(40% 40% 40% 40%)' },
				{ clipPath: 'inset(0% 0% 0% 0%)', duration: 1.0, ease: 'power3.inOut' }
			);

			// Overlay appears
			tl.from('.hero-overlay', {
				opacity: 0,
				duration: 0.6,
				ease: 'power2.out'
			}, '-=0.8');

			// Brand logo
			tl.from('.hero-brand', {
				opacity: 0,
				scale: 0.6,
				filter: 'blur(10px)',
				duration: 0.7,
				ease: 'power3.out'
			}, '-=0.4');

			// Kicker text — letter by letter
			const kickerChars = heroEl.querySelectorAll('.hero-kicker .kicker-char');
			tl.from(kickerChars, {
				opacity: 0,
				y: 12,
				duration: 0.3,
				ease: 'power3.out',
				stagger: 0.018
			}, '-=0.4');

			// Title — word by word reveal with clip-path
			const titleWords = heroEl.querySelectorAll('.hero-title .word-wrap');
			tl.from(titleWords, {
				y: '100%',
				duration: 0.7,
				ease: 'power4.out',
				stagger: 0.06
			}, '-=0.3');

			// Gold italic emphasis — shimmer
			tl.from('.hero-title em', {
				color: 'rgba(245, 245, 240, 1)',
				textShadow: '0 0 0px transparent',
				duration: 0.5,
				ease: 'power2.out'
			}, '-=0.3');

			tl.to('.hero-title em', {
				textShadow: '0 0 20px rgba(201, 163, 71, 0.3)',
				duration: 0.7,
				ease: 'power2.inOut',
				yoyo: true,
				repeat: 1
			}, '-=0.2');

			// Golden rule line expands from center
			tl.from('.hero-rule', {
				scaleX: 0,
				duration: 0.6,
				ease: 'power3.inOut'
			}, '-=1.0');

			// Subtitle
			tl.from('.hero-sub', {
				opacity: 0,
				y: 20,
				filter: 'blur(4px)',
				duration: 0.6,
				ease: 'power3.out'
			}, '-=0.5');

			// Buttons with stagger and slight 3D rotation
			const btns = heroEl.querySelectorAll('.hero-btns a');
			tl.from(btns, {
				opacity: 0,
				y: 25,
				rotateX: 12,
				duration: 0.5,
				ease: 'power3.out',
				stagger: 0.08
			}, '-=0.3');

			// Watermark text
			tl.from('.hero-watermark', {
				opacity: 0,
				x: 40,
				duration: 0.9,
				ease: 'power2.out'
			}, '-=0.7');
		};

		if (entranceDone) {
			initAnimations();
		} else {
			window.addEventListener('entrance-complete', () => initAnimations(), { once: true });
		}

		// === SCROLL-BASED PARALLAX ===
		// Video moves slower than content (parallax)
		gsap.to(videoEl, {
			y: '20%',
			ease: 'none',
			scrollTrigger: {
				trigger: heroEl,
				start: 'top top',
				end: 'bottom top',
				scrub: true
			}
		});

		// Watermark parallax (moves opposite)
		gsap.to('.hero-watermark', {
			y: '-30%',
			ease: 'none',
			scrollTrigger: {
				trigger: heroEl,
				start: 'top top',
				end: 'bottom top',
				scrub: true
			}
		});

		// Content fades out on scroll
		gsap.to('.hero-content', {
			opacity: 0,
			y: -60,
			ease: 'none',
			scrollTrigger: {
				trigger: heroEl,
				start: '60% top',
				end: 'bottom top',
				scrub: true
			}
		});
	});
</script>

<section id="hero" class="hero" bind:this={heroEl}>
	<video class="hero-video" bind:this={videoEl} autoplay muted loop playsinline>
		<source src="/videos/video_banner.mp4" type="video/mp4" />
	</video>
	<div class="hero-overlay"></div>
	<div class="hero-watermark">PROMISES</div>
	<div class="hero-inner">
		<div class="hero-content">
			<div class="hero-brand">
				<img src="/imgs/logo-removebg.png" alt="White Lace & Promises" />
			</div>
			<p class="hero-kicker">
				{#each 'WEDDING & EVENT STYLING'.split('') as char}
					<span class="kicker-char">{char === ' ' ? '\u00A0' : char}</span>
				{/each}
			</p>
			<h1 class="hero-title">
				<span class="word-line">
					<span class="word-wrap">Designed</span>
				</span>
				<span class="word-line">
					<span class="word-wrap">&nbsp;with</span>
				</span>
				<span class="word-line">
					<span class="word-wrap">&nbsp;Grace,</span>
				</span>
				<br />
				<span class="word-line">
					<span class="word-wrap">Styled</span>
				</span>
				<span class="word-line">
					<span class="word-wrap">&nbsp;with</span>
				</span>
				<span class="word-line">
					<span class="word-wrap">&nbsp;<em>Heart</em></span>
				</span>
			</h1>
			<div class="hero-rule"></div>
			<p class="hero-sub">
				Step into a world of elegance, charm, and unforgettable moments.<br />
				White Lace & Promises brings celebrations to life with styling, planning and detail-rich
				design.
			</p>
			<div class="hero-btns">
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
		height: 100vh;
		min-height: 600px;
		overflow: hidden;
	}
	.hero-video {
		position: absolute;
		inset: 0;
		width: 100%;
		height: 120%;
		object-fit: cover;
		filter: grayscale(100%) brightness(0.86) contrast(0.96);
		will-change: transform;
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
		will-change: transform;
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
		will-change: transform, opacity;
	}
	.hero-brand {
		width: 192px;
		height: 108px;
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
		display: flex;
		justify-content: center;
		flex-wrap: wrap;
	}
	:global(.kicker-char) {
		display: inline-block;
	}
	.hero-title {
		font-family: var(--font-heading);
		font-size: clamp(3rem, 5.8vw, 5.45rem);
		font-weight: 300;
		line-height: 1.02;
		color: var(--off-white);
		margin-top: 16px;
		perspective: 800px;
	}
	.word-line {
		display: inline-block;
		overflow: hidden;
		vertical-align: bottom;
	}
	.word-wrap {
		display: inline-block;
		will-change: transform;
	}
	.hero-title :global(em) {
		font-style: italic;
		color: var(--gold);
	}
	.hero-rule {
		width: min(24vw, 220px);
		height: 1px;
		margin: 24px auto 22px;
		background: linear-gradient(to right, transparent, var(--gold), transparent);
		transform-origin: center;
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
		perspective: 600px;
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
			height: 100vh;
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
			width: 154px;
			height: 86px;
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
