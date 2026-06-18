<script module lang="ts">
	let hasPlayedThisAppLoad = false;
</script>

<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';

	let container = $state<HTMLDivElement>();
	let done = $state(hasPlayedThisAppLoad);

	onMount(() => {
		if (hasPlayedThisAppLoad) {
			done = true;
			(window as Window & { __wlpEntrancePlayed?: boolean }).__wlpEntrancePlayed = true;
			window.dispatchEvent(new CustomEvent('entrance-complete'));
			return;
		}

		if (!container) return;

		const tl = gsap.timeline({
			onComplete: () => {
				hasPlayedThisAppLoad = true;
				(window as Window & { __wlpEntrancePlayed?: boolean }).__wlpEntrancePlayed = true;
				done = true;
				window.dispatchEvent(new CustomEvent('entrance-complete'));
			}
		});

		const corners = container.querySelectorAll('.corner-bracket');
		const brandName = container.querySelector('.brand-name');
		const brandGlow = container.querySelector('.brand-glow');
		const tagline = container.querySelector('.entrance-tagline');
		const horizontalLines = container.querySelectorAll('.h-line');
		const verticalLines = container.querySelectorAll('.v-line');
		const logoImg = container.querySelector('.entrance-logo-img');
		const veil = container.querySelector('.entrance-veil');

		// Set initial states for clean GSAP animations
		gsap.set(corners, { opacity: 0, scale: 0.85 });
		gsap.set(brandName, { opacity: 0, scale: 0.8, filter: 'blur(15px)' });
		gsap.set(brandGlow, { scale: 0.5, opacity: 0 });
		gsap.set(tagline, { opacity: 0, y: 20, letterSpacing: '0.15em', filter: 'blur(8px)' });
		gsap.set(horizontalLines, { scaleX: 0 });
		gsap.set(verticalLines, { scaleY: 0 });
		gsap.set(logoImg, { opacity: 0, y: -20, filter: 'blur(10px)' });

		// Act 1: Draw the luxury framing lines
		tl.to(horizontalLines, {
			scaleX: 1,
			duration: 1.5,
			ease: 'power3.inOut',
			stagger: 0.1
		});
		tl.to(verticalLines, {
			scaleY: 1,
			duration: 1.5,
			ease: 'power3.inOut',
			stagger: 0.1
		}, '-=1.5');

		// Act 2: Corner brackets materialize
		tl.to(corners, {
			opacity: 0.85,
			scale: 1,
			duration: 1.4,
			ease: 'power2.out',
			stagger: 0.08
		}, '-=1.2');

		// Act 3: Small Crown Emblem drops down
		tl.to(logoImg, {
			opacity: 0.8,
			y: 0,
			filter: 'blur(0px)',
			duration: 1.2,
			ease: 'power3.out'
		}, '-=0.8');

		// Act 4: The Company Name expands (scales up) and reveals with blur-to-sharp
		tl.to(brandName, {
			opacity: 1,
			scale: 1.05,
			filter: 'blur(0px)',
			duration: 2.5,
			ease: 'power2.out'
		}, '-=0.8');

		// Animate the gold sweep background positioning inside the text
		tl.to('.brand-name', {
			backgroundPosition: '200% center',
			duration: 3.5,
			ease: 'none'
		}, '-=2.5');

		tl.to(brandGlow, {
			opacity: 0.5,
			scale: 1.3,
			duration: 2.8,
			ease: 'power2.out'
		}, '-=3.0');

		// Act 5: Spaced Tagline fades and expands below
		tl.to(tagline, {
			opacity: 1,
			y: 0,
			letterSpacing: '0.35em',
			filter: 'blur(0px)',
			duration: 2.2,
			ease: 'power3.out'
		}, '-=1.8');

		// Act 6: Luxury hold / appreciation moment
		tl.to({}, { duration: 1.2 });

		// Act 7: Outro transition (Iris circular wipe)
		tl.to(container.querySelector('.center-assembly'), {
			scale: 1.1,
			opacity: 0,
			duration: 1.5,
			ease: 'power3.inOut'
		});

		tl.to(veil, {
			clipPath: 'circle(0% at 50% 50%)',
			duration: 2.0,
			ease: 'power4.inOut'
		}, '-=1.3');
	});
</script>

{#if !done}
	<div class="entrance-overlay" bind:this={container}>
		<!-- Luxury Dark Velvet Veil -->
		<div class="entrance-veil">
			<!-- Soft warm background light glow -->
			<div class="brand-glow"></div>

			<!-- Core Assembly (Perfect centering container) -->
			<div class="center-assembly">
				<!-- Outer Decorative Luxury Frame -->
				<div class="luxury-frame">
					<div class="corner-bracket tl"></div>
					<div class="corner-bracket tr"></div>
					<div class="corner-bracket bl"></div>
					<div class="corner-bracket br"></div>
					
					<!-- Thin border lines -->
					<div class="v-line left-vline"></div>
					<div class="v-line right-vline"></div>
					<div class="h-line top-hline"></div>
					<div class="h-line bottom-hline"></div>
				</div>

				<!-- Content Wrapper -->
				<div class="content-wrapper">
					<!-- Small Elegant Gold Crown / Crest Logo -->
					<div class="logo-wrapper">
						<img class="entrance-logo-img" src="/imgs/logo-removebg.png" alt="White Lace & Promises Crest" />
					</div>

					<!-- Massive Striking Brand Name with liquid gold animation inside -->
					<h1 class="brand-name">
						WHITE LACE & PROMISES
					</h1>

					<!-- Spaced Tagline -->
					<p class="entrance-tagline">
						Where your story becomes timeless
					</p>
				</div>
			</div>
		</div>

		<!-- Fine gold dust particles -->
		<div class="entrance-particles">
			{#each Array(40) as _, i}
				<div class="particle" style="--delay: {i * 0.25}s; --x: {Math.random() * 100}%; --y: {Math.random() * 100}%; --size: {0.8 + Math.random() * 1.6}px;"></div>
			{/each}
		</div>
	</div>
{/if}

<style>
	.entrance-overlay {
		position: fixed;
		inset: 0;
		z-index: 9999;
		pointer-events: none;
	}
	
	.entrance-veil {
		position: absolute;
		inset: 0;
		background: radial-gradient(circle at center, #0e0d0b 0%, #060606 100%);
		display: flex;
		align-items: center;
		justify-content: center;
		clip-path: circle(150% at 50% 50%);
		pointer-events: all;
		overflow: hidden;
	}

	/* Soft gold radial glow */
	.brand-glow {
		position: absolute;
		width: 500px;
		height: 500px;
		background: radial-gradient(circle, rgba(201, 163, 71, 0.08) 0%, transparent 70%);
		pointer-events: none;
	}

	/* Center Assembly (perfectly centered box) */
	.center-assembly {
		position: relative;
		display: flex;
		align-items: center;
		justify-content: center;
		width: min(780px, 90vw);
		height: 400px;
	}

	/* Intricate Luxury Frame */
	.luxury-frame {
		position: absolute;
		inset: 0;
		pointer-events: none;
	}
	
	.corner-bracket {
		position: absolute;
		width: 32px;
		height: 32px;
		border-color: rgba(201, 163, 71, 0.75);
		border-style: solid;
		border-width: 0;
	}
	.corner-bracket.tl { top: 0; left: 0; border-top-width: 1px; border-left-width: 1px; }
	.corner-bracket.tr { top: 0; right: 0; border-top-width: 1px; border-right-width: 1px; }
	.corner-bracket.bl { bottom: 0; left: 0; border-bottom-width: 1px; border-left-width: 1px; }
	.corner-bracket.br { bottom: 0; right: 0; border-bottom-width: 1px; border-right-width: 1px; }

	/* Connecting border lines */
	.v-line {
		position: absolute;
		top: 32px;
		width: 1px;
		height: calc(100% - 64px);
		background: rgba(201, 163, 71, 0.14);
	}
	.left-vline { left: 0; }
	.right-vline { right: 0; }

	.h-line {
		position: absolute;
		left: 32px;
		height: 1px;
		width: calc(100% - 64px);
		background: rgba(201, 163, 71, 0.14);
	}
	.top-hline { top: 0; }
	.bottom-hline { bottom: 0; }

	/* Content container layout */
	.content-wrapper {
		position: relative;
		z-index: 3;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		width: 100%;
		padding: 40px;
	}

	/* Small Crest Logo above the brand name */
	.logo-wrapper {
		width: 130px;
		height: 92px;
		display: flex;
		align-items: center;
		justify-content: center;
		margin-bottom: 30px;
	}
	.entrance-logo-img {
		width: 100%;
		height: 100%;
		object-fit: contain;
		filter: invert(1) grayscale(1) brightness(1.3) contrast(1.1);
		opacity: 0;
		transform: translateY(-20px);
	}

	/* Massive Brand Name with Moving liquid gold sweep inside */
	.brand-name {
		font-family: var(--font-heading, 'Cormorant Garamond', serif);
		font-size: clamp(1.55rem, 4vw, 3.25rem);
		font-weight: 300;
		letter-spacing: 0.16em;
		text-align: center;
		margin: 0;
		padding: 0;
		background: linear-gradient(
			120deg,
			#8a6f27 0%,
			#c9a347 25%,
			#f5f5f0 50%,
			#c9a347 75%,
			#8a6f27 100%
		);
		background-size: 200% auto;
		background-clip: text;
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		display: inline-block;
		text-shadow: 0 0 45px rgba(201, 163, 71, 0.15);
		opacity: 0;
		transform: scale(0.8);
		filter: blur(15px);
		will-change: transform, filter, opacity;
	}

	/* Tagline below the brand name */
	.entrance-tagline {
		font-family: var(--font-body, 'Montserrat', sans-serif);
		font-size: clamp(0.55rem, 1.2vw, 0.75rem);
		font-weight: 300;
		text-transform: uppercase;
		color: rgba(245, 245, 240, 0.65);
		letter-spacing: 0.22em;
		text-align: center;
		margin-top: 24px;
		white-space: nowrap;
		opacity: 0;
		transform: translateY(20px);
		filter: blur(8px);
	}

	/* Floating particles */
	.entrance-particles {
		position: absolute;
		inset: 0;
		overflow: hidden;
		pointer-events: none;
	}
	.particle {
		position: absolute;
		left: var(--x);
		top: var(--y);
		width: var(--size);
		height: var(--size);
		background: #e8c87d;
		border-radius: 50%;
		opacity: 0;
		animation: float-particle 5s var(--delay) ease-in-out infinite;
	}
	.brand-glow {
		opacity: 0;
		transform: scale(0.5);
	}
	.corner-bracket {
		opacity: 0;
		transform: scale(0.85);
	}
	.h-line {
		transform: scaleX(0);
		transform-origin: center;
	}
	.v-line {
		transform: scaleY(0);
		transform-origin: center;
	}
	@keyframes float-particle {
		0%, 100% { opacity: 0; transform: translateY(0) scale(0); }
		50% { opacity: 0.5; transform: translateY(-40px) scale(1.2); }
	}
</style>
