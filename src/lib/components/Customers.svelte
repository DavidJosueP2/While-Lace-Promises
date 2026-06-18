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

	const detailPhotos = photos;
	let activeIndex = $state(0);
	let feature = $derived(detailPhotos[activeIndex]);
	let portrait = $derived(activeIndex === 0 ? photos[8] : detailPhotos[(activeIndex + 1) % detailPhotos.length]);
</script>

<section id="customers" class="customers">
	<div class="customers-inner">
		<div class="customers-copy">
			<p class="section-label fade-up">OUR CHERISHED COUPLES</p>
			<h2 class="customers-heading fade-up delay-1">
				Moments We've Been<br /><em>Honoured</em> to Share
			</h2>
			<p class="customers-text fade-up delay-2">
				A quiet collection of love stories, joyful details, and celebrations remembered long
				after the last candle fades.
			</p>
			<div class="customers-note fade-up delay-3">
				<span>You're Cared For</span>
				<p>We take care of the details so you can feel calm, held, and fully present.</p>
			</div>
		</div>

		<div class="customers-showcase fade-up delay-2">
			<div class="feature-frame">
				{#key feature}
					<img src={feature} alt="White Lace and Promises couple celebration" loading="lazy" />
				{/key}
			</div>
			<div class="portrait-frame">
				{#key portrait}
					<img src={portrait} alt="Elegant White Lace and Promises event moment" loading="lazy" />
				{/key}
			</div>
			<div class="moment-strip" aria-label="Selected celebration moments">
				{#each detailPhotos as src, i}
					<button
						type="button"
						class="moment-thumb"
						class:active={activeIndex === i}
						aria-label="Show celebration moment {i + 1}"
						onclick={() => (activeIndex = i)}
					>
						<img {src} alt="White Lace and Promises celebration detail {i + 1}" loading="lazy" />
					</button>
				{/each}
			</div>
		</div>

		<div class="mobile-moments fade-up delay-3">
			{#each [photos[0], photos[8], ...detailPhotos.slice(1, 5)] as src, i}
				<div class="mobile-moment">
					<img {src} alt="White Lace and Promises couple moment {i + 1}" loading="lazy" />
				</div>
			{/each}
		</div>
	</div>
	<Ornament />
</section>

<style>
	.customers {
		background: var(--dark-card);
		padding: 100px 48px 0;
	}
	.customers-inner {
		display: grid;
		grid-template-columns: 0.78fr 1.22fr;
		gap: 70px;
		align-items: center;
		max-width: 1300px;
		margin: 0 auto;
	}
	.customers-copy {
		position: relative;
		z-index: 2;
	}
	.customers-heading {
		font-family: var(--font-heading);
		font-size: clamp(2.4rem, 5vw, 4.3rem);
		font-weight: 300;
		line-height: 1.08;
		color: var(--off-white);
		margin-top: 16px;
	}
	.customers-heading em {
		font-style: italic;
		color: var(--gold);
	}
	.customers-text {
		font-family: var(--font-body);
		font-size: 0.86rem;
		font-weight: 300;
		line-height: 1.8;
		color: var(--light-grey);
		max-width: 420px;
		margin-top: 24px;
	}
	.customers-note {
		border-left: 1px solid var(--gold);
		padding-left: 20px;
		margin-top: 34px;
	}
	.customers-note span {
		font-family: var(--font-body);
		font-size: 0.62rem;
		font-weight: 500;
		letter-spacing: 0.26em;
		text-transform: uppercase;
		color: var(--gold);
	}
	.customers-note p {
		font-family: var(--font-heading);
		font-size: 1.35rem;
		font-weight: 300;
		line-height: 1.35;
		color: var(--off-white);
		max-width: 360px;
		margin-top: 10px;
	}
	.customers-showcase {
		position: relative;
		min-height: 620px;
	}
	.feature-frame,
	.portrait-frame,
	.moment-thumb,
	.mobile-moment {
		overflow: hidden;
		background: var(--black);
	}
	.feature-frame {
		position: absolute;
		top: 0;
		left: 4%;
		width: 62%;
		height: 520px;
	}
	.portrait-frame {
		position: absolute;
		right: 0;
		top: 78px;
		width: 38%;
		height: 438px;
		border: 10px solid var(--dark-card);
		z-index: 2;
	}
	.feature-frame img,
	.portrait-frame img,
	.moment-thumb img,
	.mobile-moment img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		transition: transform 0.7s ease;
	}
	.feature-frame img {
		animation: feature-reveal 0.62s cubic-bezier(0.23, 1, 0.32, 1);
	}
	.portrait-frame img {
		animation: portrait-reveal 0.52s cubic-bezier(0.23, 1, 0.32, 1);
	}
	.feature-frame:hover img,
	.portrait-frame:hover img,
	.moment-thumb:hover img,
	.mobile-moment:hover img {
		transform: scale(1.045);
	}
	.moment-strip {
		position: absolute;
		left: 0;
		bottom: 28px;
		display: grid;
		grid-template-columns: repeat(9, 56px);
		gap: 8px;
		padding: 10px 12px;
		background: rgba(10, 10, 10, 0.72);
		border: 1px solid rgba(201, 163, 71, 0.08);
		backdrop-filter: blur(12px);
		width: max-content;
		z-index: 3;
	}
	.moment-thumb {
		width: 56px;
		height: 78px;
		border: 1px solid transparent;
		cursor: pointer;
		padding: 0;
		transition:
			border-color 0.25s ease,
			opacity 0.25s ease,
			transform 0.25s ease;
	}
	.moment-thumb:hover,
	.moment-thumb.active {
		border-color: var(--gold);
		transform: translateY(-3px);
	}
	.moment-thumb:not(.active) {
		opacity: 0.78;
	}
	.moment-thumb:focus-visible {
		outline: 1px solid var(--gold);
		outline-offset: 4px;
	}
	.mobile-moments {
		display: none;
	}
	@keyframes feature-reveal {
		from {
			opacity: 0;
			transform: scale(1.045);
		}
		to {
			opacity: 1;
			transform: scale(1);
		}
	}
	@keyframes portrait-reveal {
		from {
			opacity: 0;
			transform: translateX(14px) scale(1.025);
		}
		to {
			opacity: 1;
			transform: translateX(0) scale(1);
		}
	}

	@media (max-width: 980px) {
		.customers-inner {
			grid-template-columns: 1fr;
			gap: 44px;
		}
		.customers-showcase {
			min-height: 560px;
		}
	}
	@media (max-width: 768px) {
		.customers {
			padding: 70px 20px 0;
		}
		.customers-showcase {
			display: none;
		}
		.mobile-moments {
			display: grid;
			grid-template-columns: repeat(2, 1fr);
			gap: 10px;
		}
		.mobile-moment {
			aspect-ratio: 4 / 5;
		}
		.mobile-moment:nth-child(3n + 1) {
			aspect-ratio: 1;
		}
	}
	@media (max-width: 480px) {
		.customers-heading {
			font-size: clamp(2.3rem, 12vw, 3.2rem);
		}
		.customers-note p {
			font-size: 1.15rem;
		}
	}
</style>
