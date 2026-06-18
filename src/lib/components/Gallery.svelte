<script lang="ts">
	const images = [
		'/imgs/619567145_18100573348880661_4118419258896769483_n.jpg',
		'/imgs/621728882_18099922351846218_5043613633722157739_n.jpg',
		'/imgs/628174667_18411193750131886_5995405509419098453_n.jpg',
		'/imgs/638987262_18566530309050662_1557370116413280739_n.jpg',
		'/imgs/648279418_18075139742136597_8694463329305322773_n.jpg',
		'/imgs/649103981_18105190270867471_356966879460120322_n.jpg',
		'/imgs/649708940_18098469499767000_3055476171050820726_n.jpg',
		'/imgs/654696516_18336535564300447_6008051749444092425_n.jpg',
		'/imgs/655110898_18366807037204825_4944429461092048334_n.jpg',
		'/imgs/once_in_life.jpg'
	];

	const carouselImages = [...images, ...images];
</script>

<section id="gallery" class="gallery">
	<div class="gallery-header">
		<div class="gallery-title-area fade-up">
			<h2 class="gallery-heading">
				A Glimpse of<br /><em>White Lace & Promises</em>
			</h2>
		</div>
		<a href="/gallery" class="gallery-btn fade-up delay-1">FULL GALLERY</a>
	</div>
	<div
		class="gallery-scroll fade-up delay-2"
		aria-label="White Lace & Promises gallery preview"
	>
		<div class="gallery-track">
			{#each carouselImages as src, i}
				<div class="gallery-item" class:tall={i % 3 === 0} data-index={i}>
					<img
						{src}
						alt="White Lace & Promises styled celebration - image {(i % images.length) + 1}"
						loading="lazy"
					/>
				</div>
			{/each}
		</div>
	</div>
</section>

<style>
	.gallery {
		background: var(--black);
		padding: 80px 0 0;
		overflow: hidden;
	}
	.gallery-header {
		display: flex;
		align-items: flex-end;
		justify-content: space-between;
		max-width: 1300px;
		margin: 0 auto 40px;
		padding: 0 48px;
	}
	.gallery-heading {
		font-family: var(--font-heading);
		font-size: clamp(2rem, 4vw, 3.2rem);
		font-weight: 300;
		line-height: 1.2;
		color: var(--off-white);
	}
	.gallery-heading em {
		font-style: italic;
		color: var(--gold);
	}
	.gallery-btn {
		font-family: var(--font-body);
		font-size: 0.6rem;
		font-weight: 500;
		letter-spacing: 0.2em;
		color: var(--gold);
		border: 1px solid var(--gold);
		padding: 12px 28px;
		white-space: nowrap;
		transition:
			background 0.3s,
			color 0.3s;
	}
	.gallery-btn:hover {
		background: var(--gold);
		color: var(--black);
	}
	.gallery-scroll {
		overflow: hidden;
		padding: 0 48px 8px;
		-ms-overflow-style: none;
		scrollbar-width: none;
	}
	.gallery-scroll::-webkit-scrollbar {
		display: none;
	}
	.gallery-track {
		display: flex;
		gap: 12px;
		width: max-content;
		animation: gallery-loop 78s linear infinite;
	}
	.gallery-scroll:hover .gallery-track {
		animation-play-state: paused;
	}
	.gallery-item {
		flex: 0 0 auto;
		width: 280px;
		height: 360px;
		overflow: hidden;
	}
	.gallery-item.tall {
		height: 420px;
	}
	.gallery-item img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		transition: transform 0.5s ease;
	}
	.gallery-item:hover img {
		transform: scale(1.05);
	}
	@keyframes gallery-loop {
		from {
			transform: translateX(0);
		}
		to {
			transform: translateX(calc(-50% - 6px));
		}
	}
	@media (max-width: 768px) {
		.gallery-header {
			flex-direction: column;
			align-items: flex-start;
			gap: 20px;
			padding: 0 20px;
		}
		.gallery-scroll {
			padding: 0 20px 8px;
		}
		.gallery-item {
			width: 220px;
			height: 300px;
		}
		.gallery-item.tall {
			height: 340px;
		}
	}
</style>
