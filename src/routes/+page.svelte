<script lang="ts">
	import Nav from '$lib/components/Nav.svelte';
	import Hero from '$lib/components/Hero.svelte';
	import About from '$lib/components/About.svelte';
	import Explore from '$lib/components/Explore.svelte';
	import Gallery from '$lib/components/Gallery.svelte';
	import Customers from '$lib/components/Customers.svelte';
	import Contact from '$lib/components/Contact.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import AmbientMusic from '$lib/components/AmbientMusic.svelte';

	let scrollY = $state(0);

	$effect(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						entry.target.classList.add('visible');
					}
				});
			},
			{ threshold: 0.1, rootMargin: '0px 0px -40px 0px' }
		);

		const elements = document.querySelectorAll('.fade-up');
		elements.forEach((el) => observer.observe(el));

		return () => observer.disconnect();
	});
</script>

<svelte:window bind:scrollY />

<Nav {scrollY} />
<Hero />
<About />
<Explore />
<Gallery />
<Customers />
<Contact />
<Footer />
<AmbientMusic />

