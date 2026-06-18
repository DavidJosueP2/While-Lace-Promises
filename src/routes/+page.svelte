<script lang="ts">
	import { onMount } from 'svelte';
	import Nav from '$lib/components/Nav.svelte';
	import Hero from '$lib/components/Hero.svelte';
	import About from '$lib/components/About.svelte';
	import Explore from '$lib/components/Explore.svelte';
	import Gallery from '$lib/components/Gallery.svelte';
	import Customers from '$lib/components/Customers.svelte';
	import Contact from '$lib/components/Contact.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import AmbientMusic from '$lib/components/AmbientMusic.svelte';
	import GrandEntrance from '$lib/components/GrandEntrance.svelte';

	let scrollY = $state(0);

	onMount(async () => {
		const gsapModule = await import('gsap');
		const scrollTriggerModule = await import('gsap/ScrollTrigger');
		const gsapAny = gsapModule as any;
		const scrollTriggerAny = scrollTriggerModule as any;
		const gsap = gsapAny.gsap ?? gsapAny.default;
		const ScrollTrigger =
			scrollTriggerAny.ScrollTrigger ??
			scrollTriggerAny.default?.ScrollTrigger ??
			scrollTriggerAny.default;

		gsap.registerPlugin(ScrollTrigger);

		// === GSAP ScrollTrigger for all .fade-up elements ===
		const fadeUpElements = document.querySelectorAll('.fade-up');
		fadeUpElements.forEach((el) => {
			let delay = 0;
			if (el.classList.contains('delay-1')) delay = 0.08;
			if (el.classList.contains('delay-2')) delay = 0.15;
			if (el.classList.contains('delay-3')) delay = 0.22;
			if (el.classList.contains('delay-4')) delay = 0.28;
			if (el.classList.contains('delay-5')) delay = 0.35;

			gsap.from(el, {
				opacity: 0,
				y: 35,
				duration: 0.7,
				delay,
				ease: 'power3.out',
				scrollTrigger: {
					trigger: el,
					start: 'top 90%',
					toggleActions: 'play none none none'
				}
			});
		});

		// === SECTION-SPECIFIC ANIMATIONS (only for non-fade-up elements) ===

		// About — image curtain reveal
		const aboutImages = document.querySelectorAll('#about .image-frame');
		aboutImages.forEach((frame) => {
			gsap.from(frame, {
				clipPath: 'inset(100% 0% 0% 0%)',
				duration: 0.9,
				ease: 'power4.inOut',
				scrollTrigger: {
					trigger: frame,
					start: 'top 85%',
					toggleActions: 'play none none none'
				}
			});
			const img = frame.querySelector('img');
			if (img) {
				gsap.from(img, {
					scale: 1.2,
					duration: 1.1,
					ease: 'power2.out',
					scrollTrigger: {
						trigger: frame,
						start: 'top 85%',
						toggleActions: 'play none none none'
					}
				});
			}
		});

		// About — vertical text
		const verticalText = document.querySelector('#about .vertical-text');
		if (verticalText) {
			gsap.from(verticalText, {
				opacity: 0,
				y: 30,
				duration: 0.8,
				ease: 'power3.out',
				scrollTrigger: {
					trigger: verticalText,
					start: 'top 90%',
					toggleActions: 'play none none none'
				}
			});
		}

		// Explore — the full card group opens from the center
		const cardsGroup = document.querySelector('#explore .cards');
		if (cardsGroup) {
			gsap.fromTo(
				cardsGroup,
				{
					clipPath: 'inset(0 50% 0 50%)',
					filter: 'brightness(0.88) blur(2px)'
				},
				{
					clipPath: 'inset(0 0% 0 0%)',
					filter: 'brightness(1) blur(0px)',
					duration: 1.25,
					ease: 'power4.inOut',
					scrollTrigger: {
						trigger: cardsGroup,
						start: 'top 88%',
						toggleActions: 'play none none none'
					}
				}
			);
		}

		// Gallery — scroll-linked speed
		const galleryTrack = document.querySelector('#gallery .gallery-track');
		if (galleryTrack) {
			ScrollTrigger.create({
				trigger: '#gallery',
				start: 'top bottom',
				end: 'bottom top',
				onUpdate: (self) => {
					const track = galleryTrack as HTMLElement;
					const speed = 1 + self.progress * 0.45;
					track.style.animationDuration = `${135 / speed}s`;
				}
			});
		}

		// Customers — image reveal
		const customerFrames = document.querySelectorAll('#customers .feature-frame, #customers .portrait-frame');
		customerFrames.forEach((frame, i) => {
			gsap.from(frame, {
				clipPath: i === 0 ? 'inset(0% 100% 0% 0%)' : 'inset(0% 0% 0% 100%)',
				duration: 1.0,
				ease: 'power4.inOut',
				scrollTrigger: {
					trigger: frame,
					start: 'top 85%',
					toggleActions: 'play none none none'
				}
			});
		});

		// Ornament dividers
		const ornaments = document.querySelectorAll('.ornament');
		ornaments.forEach((orn) => {
			const lines = orn.querySelectorAll('.orn-line');
			const dot = orn.querySelector('.orn-dot');
			if (lines.length && dot) {
				const ornTl = gsap.timeline({
					scrollTrigger: {
						trigger: orn,
						start: 'top 92%',
						toggleActions: 'play none none none'
					}
				});
				ornTl.from(dot, { scale: 0, rotate: 180, duration: 0.4, ease: 'back.out(1.7)' });
				ornTl.from(lines, { scaleX: 0, duration: 0.6, ease: 'power3.out', stagger: 0.08 }, '-=0.2');
			}
		});

		// Nav — slide in after entrance
		const nav = document.querySelector('.nav');
		if (nav) {
			const entranceDone = (window as Window & { __wlpEntrancePlayed?: boolean }).__wlpEntrancePlayed;
			if (!entranceDone) {
				gsap.set(nav, { y: -100, opacity: 0 });
				window.addEventListener('entrance-complete', () => {
					gsap.to(nav, {
						y: 0,
						opacity: 1,
						duration: 0.8,
						delay: 0.2,
						ease: 'power3.out'
					});
				}, { once: true });
			}
		}
	});
</script>

<svelte:window bind:scrollY />

<GrandEntrance />
<Nav {scrollY} />
<Hero />
<About />
<Explore />
<Gallery />
<Customers />
<Contact />
<Footer />
<AmbientMusic />
