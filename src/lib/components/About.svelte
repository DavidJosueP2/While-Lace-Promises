
<section id="about" class="about">
	<div class="about-inner">
		<div class="about-side">
			<span class="vertical-text">OUR STORY</span>
		</div>
		<div class="about-content">
			<p class="section-label fade-up">WHITE LACE & PROMISES, AUSTRALIA</p>
			<h2 class="about-heading fade-up delay-1">
				More than styling —<br />it's where <em>memories</em><br />last a lifetime
			</h2>
			<p class="body-text fade-up delay-2">
				Brisbane Based Wedding and Event Stylist, event planning, consulting, designer and
				execution specialist. For luxuriously themed & styled events.
			</p>
			<p class="body-text fade-up delay-3">
				What began as a love for beautiful details has grown into a passion for creating
				celebrations that feel heartfelt, welcoming, and truly memorable.
			</p>
			<a href="#contact" class="story-link fade-up delay-4">
				OUR STORY <span class="arrow">⟶</span>
			</a>
		</div>
		<div class="about-image fade-up delay-2">
			<img src="/imgs/once_in_life.jpg" alt="White Lace and Promises styled event interior" />
		</div>
	</div>
</section>

<style>
	.about {
		background: var(--black);
		padding: 100px 48px 120px;
	}
	.about-inner {
		display: grid;
		grid-template-columns: 40px 1fr 1fr;
		gap: 60px;
		max-width: 1300px;
		margin: 0 auto;
		align-items: center;
	}
	.about-side {
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.vertical-text {
		writing-mode: vertical-rl;
		transform: rotate(180deg);
		font-family: var(--font-body);
		font-size: 0.6rem;
		font-weight: 400;
		letter-spacing: 0.3em;
		color: var(--grey);
		text-transform: uppercase;
		border-right: 1px solid rgba(153, 153, 153, 0.3);
		padding-right: 12px;
	}
	.about-content {
		display: flex;
		flex-direction: column;
		gap: 20px;
	}
	.about-heading {
		font-family: var(--font-heading);
		font-size: clamp(2rem, 4vw, 3.2rem);
		font-weight: 300;
		line-height: 1.2;
		color: var(--off-white);
	}
	.about-heading em {
		font-style: italic;
		color: var(--gold);
	}
	.story-link {
		font-family: var(--font-body);
		font-size: 0.7rem;
		font-weight: 400;
		letter-spacing: 0.2em;
		color: var(--off-white);
		display: inline-flex;
		align-items: center;
		gap: 10px;
		margin-top: 8px;
		transition: color 0.3s;
	}
	.story-link:hover {
		color: var(--gold);
	}
	.arrow {
		font-size: 1rem;
	}
	.about-image {
		overflow: hidden;
	}
	.about-image img {
		width: 100%;
		height: 500px;
		object-fit: cover;
		transition: transform 0.6s ease;
	}
	.about-image:hover img {
		transform: scale(1.03);
	}

	@media (max-width: 900px) {
		.about {
			padding: 60px 20px 80px;
		}
		.about-inner {
			grid-template-columns: 1fr;
			gap: 32px;
		}
		.about-side {
			display: none;
		}
		.about-image img {
			height: 350px;
		}
	}
</style>
