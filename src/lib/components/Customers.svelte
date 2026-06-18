<script lang="ts">
	import Ornament from '$lib/components/Ornament.svelte';

	const photos = [
		'/imgs/customers/508160488_1012097271137033_3118339442498118947_n.jpg',
		'/imgs/customers/530461776_739848848976170_9002161160685368363_n.jpg',
		'/imgs/customers/619178525_18059122811336298_3016849690215942174_n.jpg',
		'/imgs/customers/621402106_18106558723737508_8360643830646039431_n.jpg',
		'/imgs/customers/625345149_18406365667132829_2278283810500225946_n.jpg',
		'/imgs/customers/625374135_18314855614301808_6389597390727461927_n.jpg',
		'/imgs/customers/629827741_18406856398123969_5280693094193732835_n.jpg',
		'/imgs/customers/633396645_18379692787087138_5594940544276362204_n.jpg',
		'/imgs/customers/655165830_18342194317242866_1188183942736511500_n.jpg'
	];
</script>

<section id="customers" class="customers">
	<div class="customers-inner">
		<p class="section-label fade-up">OUR CHERISHED COUPLES</p>
		<h2 class="customers-heading fade-up delay-1">
			Moments We've Been<br /><em>Honoured</em> to Share
		</h2>
		<div class="photo-grid fade-up delay-2">
			{#each photos as src, i}
				<div class="photo-item">
					<img {src} alt="Happy couple {i + 1}" loading="lazy" />
				</div>
			{/each}
		</div>
	</div>
	<Ornament />
</section>

<style>
	.customers {
		background: var(--dark-card);
		padding: 80px 48px 0;
	}
	.customers-inner {
		max-width: 1100px;
		margin: 0 auto;
		text-align: center;
	}
	.customers-heading {
		font-family: var(--font-heading);
		font-size: clamp(2rem, 4vw, 3.2rem);
		font-weight: 300;
		line-height: 1.2;
		color: var(--off-white);
		margin-top: 16px;
		margin-bottom: 48px;
	}
	.customers-heading em {
		font-style: italic;
		color: var(--gold);
	}
	.photo-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 12px;
	}
	.photo-item {
		overflow: hidden;
		aspect-ratio: 1;
		position: relative;
	}
	.photo-item::after {
		content: '';
		position: absolute;
		inset: 0;
		border: 2px solid transparent;
		transition: border-color 0.4s ease;
		pointer-events: none;
	}
	.photo-item:hover::after {
		border-color: var(--gold);
	}
	.photo-item img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		transition: transform 0.5s ease;
	}
	.photo-item:hover img {
		transform: scale(1.06);
	}

	@media (max-width: 768px) {
		.customers { padding: 60px 20px 0; }
		.photo-grid { grid-template-columns: repeat(2, 1fr); }
	}
	@media (max-width: 480px) {
		.photo-grid { grid-template-columns: repeat(2, 1fr); gap: 8px; }
	}
</style>
