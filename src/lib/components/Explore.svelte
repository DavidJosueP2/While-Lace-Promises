<script lang="ts">
	import Ornament from '$lib/components/Ornament.svelte';

	const services = [
		{
			num: '01',
			title: 'Weddings',
			desc: 'Crystal chandeliers, floral grandeur, and a dance floor made for your first moments together.',
			img: '/imgs/619567145_18100573348880661_4118419258896769483_n.jpg',
			href: '/events/weddings'
		},
		{
			num: '02',
			title: 'Corporate Events',
			desc: 'Elevate your brand with a setting that speaks volumes before a word is said.',
			img: '/imgs/628174667_18411193750131886_5995405509419098453_n.jpg',
			href: '/events/corporate-events'
		},
		{
			num: '03',
			title: 'Social Celebrations',
			desc: 'Baby showers, milestone birthdays, engagements — every occasion deserves to be extraordinary.',
			img: '/imgs/649103981_18105190270867471_356966879460120322_n.jpg',
			href: '/events/social-celebrations'
		},
		{
			num: '04',
			title: 'Special Occasions',
			desc: 'Cultural ceremonies, anniversaries, private dinners — crafted with reverence and elegance.',
			img: '/imgs/654696516_18336535564300447_6008051749444092425_n.jpg',
			href: '/events/special-occasions'
		}
	];
</script>

<section id="explore" class="explore">
	<div class="explore-header">
		<p class="section-label fade-up">EXPLORE WHITE LACE & PROMISES</p>
		<h2 class="explore-title fade-up delay-1">
			Every Chapter of<br /><em>Your Celebration</em>
		</h2>
	</div>
	<section class="feature-image fade-up delay-2" aria-label="Styled celebration table setting"></section>
	<div class="cards">
		{#each services as svc, i}
			<a href={svc.href} class="card fade-up delay-{i + 1}">
				<img src={svc.img} alt={svc.title} class="card-img" />
				<div class="card-overlay"></div>
				<div class="card-content">
					<span class="card-num">{svc.num}</span>
					<h3 class="card-title">{svc.title}</h3>
					<p class="card-desc">{svc.desc}</p>
					<span class="card-arrow">⟶</span>
				</div>
			</a>
		{/each}
	</div>
	<Ornament />
</section>

<style>
	.explore {
		background: var(--dark-card);
		padding: 80px 48px 0;
	}
	.explore-header {
		text-align: center;
		max-width: 700px;
		margin: 0 auto 42px;
	}
	.explore-title {
		font-family: var(--font-heading);
		font-size: clamp(2rem, 4vw, 3.2rem);
		font-weight: 300;
		line-height: 1.2;
		color: var(--off-white);
		margin-top: 16px;
	}
	.explore-title em {
		font-style: italic;
		color: var(--gold);
	}
	.feature-image {
		position: relative;
		min-height: clamp(360px, 58vw, 720px);
		margin: 0 calc(50% - 50vw) 64px;
		background:
			linear-gradient(to bottom, rgba(10, 10, 10, 0.1), rgba(10, 10, 10, 0.38)),
			url('/imgs/once_in_life.jpg') center / cover no-repeat;
	}
	.feature-image::after {
		content: '';
		position: absolute;
		inset: 0;
		border-top: 1px solid rgba(201, 163, 71, 0.26);
		border-bottom: 1px solid rgba(201, 163, 71, 0.26);
		pointer-events: none;
	}
	.cards {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 16px;
		max-width: 1300px;
		margin: 0 auto;
	}
	.card {
		position: relative;
		overflow: hidden;
		aspect-ratio: 3 / 4;
		display: flex;
		align-items: flex-end;
		text-decoration: none;
		cursor: pointer;
	}
	.card-img {
		position: absolute;
		inset: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
		transition: transform 0.6s ease;
	}
	.card:hover .card-img {
		transform: scale(1.08);
	}
	.card-overlay {
		position: absolute;
		inset: 0;
		background: linear-gradient(to top, rgba(0,0,0,0.8) 0%, rgba(0,0,0,0.1) 60%);
		transition: background 0.4s;
	}
	.card:hover .card-overlay {
		background: linear-gradient(to top, rgba(0,0,0,0.9) 0%, rgba(0,0,0,0.2) 60%);
	}
	.card-content {
		position: relative;
		z-index: 2;
		padding: 24px;
		width: 100%;
	}
	.card-num {
		font-family: var(--font-heading);
		font-size: 3rem;
		font-weight: 300;
		color: rgba(245, 245, 240, 0.12);
		line-height: 1;
	}
	.card-title {
		font-family: var(--font-body);
		font-size: 0.7rem;
		font-weight: 500;
		letter-spacing: 0.2em;
		text-transform: uppercase;
		color: var(--off-white);
		margin-top: 4px;
	}
	.card-desc {
		font-family: var(--font-body);
		font-size: 0.72rem;
		font-weight: 300;
		color: var(--light-grey);
		line-height: 1.6;
		margin-top: 8px;
		opacity: 0;
		max-height: 0;
		overflow: hidden;
		transition: opacity 0.4s, max-height 0.4s;
	}
	.card:hover .card-desc {
		opacity: 1;
		max-height: 80px;
	}
	.card-arrow {
		display: inline-block;
		margin-top: 12px;
		color: var(--gold);
		font-size: 1rem;
		transition: transform 0.3s;
	}
	.card:hover .card-arrow {
		transform: translateX(6px);
	}

	@media (max-width: 900px) {
		.explore { padding: 60px 20px 0; }
		.feature-image {
			min-height: 420px;
			margin-bottom: 44px;
		}
		.cards { grid-template-columns: repeat(2, 1fr); }
	}
	@media (max-width: 500px) {
		.feature-image {
			min-height: 360px;
		}
		.cards { grid-template-columns: 1fr; }
	}
</style>
