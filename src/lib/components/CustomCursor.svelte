<script lang="ts">
	import { onMount } from 'svelte';

	const TRAIL_PARTICLES = 120;
	const trailItems = Array.from({ length: TRAIL_PARTICLES });

	let cursorCore: HTMLDivElement;
	let cursorFrame: HTMLDivElement;
	let trailLayer: HTMLDivElement;
	let visible = $state(false);
	let hovering = $state(false);

	onMount(() => {
		const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
		const isTouch = window.matchMedia('(hover: none), (pointer: coarse)').matches;

		if (prefersReducedMotion || isTouch) return;

		document.body.classList.add('custom-cursor-active');

		let mouseX = window.innerWidth / 2;
		let mouseY = window.innerHeight / 2;
		let coreX = mouseX;
		let coreY = mouseY;
		let lastTrailX = mouseX;
		let lastTrailY = mouseY;
		let particleIndex = 0;
		let raf = 0;

		const particles = Array.from(
			trailLayer.querySelectorAll<HTMLSpanElement>('.trail-pixel')
		);

		const pattern: Array<[number, number, number, number]> = [
			[-28, -16, 0.22, 5],
			[-18, -16, 0.38, 5],
			[-8, -16, 0.58, 6],
			[2, -16, 0.48, 5],
			[12, -16, 0.28, 5],
			[-34, -7, 0.28, 5],
			[-24, -7, 0.54, 6],
			[-14, -7, 0.76, 6],
			[-4, -7, 0.92, 7],
			[6, -7, 0.74, 6],
			[16, -7, 0.48, 5],
			[26, -7, 0.24, 5],
			[-34, 3, 0.26, 5],
			[-24, 3, 0.58, 6],
			[-14, 3, 0.84, 7],
			[-4, 3, 1, 7],
			[6, 3, 0.78, 6],
			[16, 3, 0.5, 6],
			[26, 3, 0.26, 5],
			[-24, 13, 0.34, 5],
			[-14, 13, 0.54, 6],
			[-4, 13, 0.68, 6],
			[6, 13, 0.48, 5],
			[16, 13, 0.26, 5]
		];

		const setPixel = (x: number, y: number, opacity: number, size: number) => {
			const pixel = particles[particleIndex];
			particleIndex = (particleIndex + 1) % particles.length;

			pixel.getAnimations().forEach((animation) => animation.cancel());
			pixel.style.width = `${size}px`;
			pixel.style.height = `${size}px`;
			pixel.style.transform = `translate3d(${x}px, ${y}px, 0) scale(1)`;
			pixel.style.opacity = `${opacity}`;

			pixel.animate(
				[
					{
						opacity: opacity * 0.95,
						transform: `translate3d(${x}px, ${y}px, 0) scale(1)`
					},
					{
						opacity: 0,
						transform: `translate3d(${x - 54}px, ${y}px, 0) scale(0.38)`
					}
				],
				{
					duration: 920,
					easing: 'cubic-bezier(0.12, 0.72, 0.18, 1)',
					fill: 'forwards'
				}
			);
		};

		const addTrailCluster = (x: number, y: number) => {
			for (const [offsetX, offsetY, opacity, size] of pattern) {
				if (Math.random() > 0.82) continue;
				setPixel(x + offsetX, y + offsetY, opacity, size);
			}
		};

		const onPointerMove = (event: PointerEvent) => {
			mouseX = event.clientX;
			mouseY = event.clientY;
			visible = true;

			const dist = Math.hypot(mouseX - lastTrailX, mouseY - lastTrailY);
			if (dist > 12) {
				addTrailCluster(mouseX, mouseY);
				lastTrailX = mouseX;
				lastTrailY = mouseY;
			}

			const target = event.target as Element | null;
			hovering = Boolean(
				target?.closest('a, button, input, select, textarea, [role="button"], .card, .moment-thumb, .gallery-item')
			);
		};

		const onPointerLeave = () => {
			visible = false;
		};

		const animate = () => {
			coreX += (mouseX - coreX) * 0.42;
			coreY += (mouseY - coreY) * 0.42;

			cursorCore.style.transform = `translate3d(${coreX}px, ${coreY}px, 0) rotate(45deg)`;
			cursorFrame.style.transform = `translate3d(${coreX}px, ${coreY}px, 0)`;

			raf = requestAnimationFrame(animate);
		};

		document.addEventListener('pointermove', onPointerMove, { passive: true });
		document.addEventListener('pointerleave', onPointerLeave);
		raf = requestAnimationFrame(animate);

		return () => {
			document.body.classList.remove('custom-cursor-active');
			document.removeEventListener('pointermove', onPointerMove);
			document.removeEventListener('pointerleave', onPointerLeave);
			cancelAnimationFrame(raf);
		};
	});
</script>

<div class="trail-layer" bind:this={trailLayer} aria-hidden="true">
	{#each trailItems as _}
		<span class="trail-pixel"></span>
	{/each}
</div>

<div class="custom-cursor" class:visible class:hovering aria-hidden="true">
	<div class="cursor-frame" bind:this={cursorFrame}></div>
	<div class="cursor-core" bind:this={cursorCore}></div>
</div>

<style>
	:global(body.custom-cursor-active),
	:global(body.custom-cursor-active *) {
		cursor: none !important;
	}

	.custom-cursor,
	.trail-layer {
		position: fixed;
		inset: 0;
		z-index: 99999;
		pointer-events: none;
	}

	.custom-cursor {
		opacity: 0;
		transition: opacity 0.18s ease;
	}

	.custom-cursor.visible {
		opacity: 1;
	}

	.cursor-core,
	.cursor-frame,
	.trail-pixel {
		position: fixed;
		top: 0;
		left: 0;
		will-change: transform, opacity;
		pointer-events: none;
	}

	.cursor-core {
		width: 8px;
		height: 8px;
		margin: -4px 0 0 -4px;
		background: #f1d57a;
		border: 1px solid rgba(10, 10, 10, 0.55);
		transform: translate3d(-100px, -100px, 0) rotate(45deg);
		box-shadow:
			0 0 0 1px rgba(245, 245, 240, 0.68),
			0 0 14px rgba(201, 163, 71, 0.46);
	}

	.cursor-frame {
		width: 28px;
		height: 28px;
		margin: -14px 0 0 -14px;
		border: 1px solid rgba(201, 163, 71, 0.78);
		transform: translate3d(-100px, -100px, 0);
		transition:
			width 0.22s ease,
			height 0.22s ease,
			margin 0.22s ease,
			border-color 0.22s ease,
			background 0.22s ease;
		box-shadow:
			0 0 0 1px rgba(10, 10, 10, 0.2),
			inset 0 0 0 1px rgba(245, 245, 240, 0.14);
	}

	.custom-cursor.hovering .cursor-frame {
		width: 42px;
		height: 42px;
		margin: -21px 0 0 -21px;
		border-color: rgba(245, 245, 240, 0.9);
		background: rgba(201, 163, 71, 0.12);
	}

	.custom-cursor.hovering .cursor-core {
		background: #ffffff;
	}

	.trail-layer {
		z-index: 99998;
	}

	.trail-pixel {
		width: 4px;
		height: 4px;
		background: rgba(245, 245, 240, 0.96);
		opacity: 0;
		transform: translate3d(-100px, -100px, 0) scale(1);
		box-shadow:
			0 0 8px rgba(245, 245, 240, 0.3),
			0 0 14px rgba(201, 163, 71, 0.22);
	}

	@media (hover: none), (pointer: coarse), (prefers-reduced-motion: reduce) {
		:global(body.custom-cursor-active),
		:global(body.custom-cursor-active *) {
			cursor: auto !important;
		}

		.custom-cursor,
		.trail-layer {
			display: none;
		}
	}
</style>
