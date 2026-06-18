<section id="about" class="about">
	<div class="about-shell">
		<div class="about-side">
			<span class="vertical-text">OUR STORY</span>
		</div>

		<div class="about-editorial">
			<div class="about-copy">
				<p class="section-label fade-up">WHITE LACE & PROMISES</p>
				<h2 class="about-heading fade-up delay-1">
					A gentle hand behind every<br /><em>beautiful moment</em>
				</h2>

				<div class="story-text fade-up delay-2">
					<p>
						Brisbane Based Wedding and Event Stylist, event planning, consulting, designer
						and execution specialist. For luxuriously themed & styled events.
					</p>
					<p>
						Our story is shaped by a love for soft details, thoughtful spaces, and the kind
						of celebrations that feel deeply personal from the moment guests arrive.
					</p>
				</div>

				<div class="story-principles fade-up delay-3">
					<div>
						<span>01</span>
						<p>Warmth before spectacle</p>
					</div>
					<div>
						<span>02</span>
						<p>Details with intention</p>
					</div>
					<div>
						<span>03</span>
						<p>Beauty that feels personal</p>
					</div>
				</div>
			</div>

			<div class="about-visual fade-up delay-2">
				<div class="image-frame main-image">
					<img src="/imgs/once_in_life.jpg" alt="White Lace and Promises styled event setting" />
				</div>
				<div class="image-frame detail-image">
					<img
						src="/imgs/649708940_18098469499767000_3055476171050820726_n.jpg"
						alt="White Lace and Promises floral styling detail"
					/>
				</div>
				<div class="visual-note">
					<span>Styling / Planning / Design</span>
					<p>Created with care for celebrations that feel effortless, romantic, and complete.</p>
				</div>
			</div>
		</div>
	</div>
</section>

<style>
	.about {
		position: relative;
		background:
			linear-gradient(135deg, rgba(20, 20, 20, 0.98), rgba(10, 10, 10, 1)),
			var(--black);
		padding: 118px 48px 130px;
		overflow: hidden;
	}
	.about::before {
		content: 'WHITE LACE';
		position: absolute;
		left: 46%;
		bottom: -0.2em;
		font-family: var(--font-heading);
		font-size: clamp(5rem, 13vw, 12rem);
		font-weight: 300;
		line-height: 1;
		color: rgba(245, 245, 240, 0.035);
		pointer-events: none;
		white-space: nowrap;
	}
	.about-shell {
		position: relative;
		z-index: 2;
		display: grid;
		grid-template-columns: 42px minmax(0, 1fr);
		gap: 54px;
		max-width: 1340px;
		margin: 0 auto;
	}
	.about-side {
		display: flex;
		align-items: stretch;
		justify-content: center;
	}
	.vertical-text {
		writing-mode: vertical-rl;
		transform: rotate(180deg);
		font-family: var(--font-body);
		font-size: 0.6rem;
		font-weight: 400;
		letter-spacing: 0.32em;
		color: var(--grey);
		text-transform: uppercase;
		border-right: 1px solid rgba(201, 163, 71, 0.38);
		padding-right: 14px;
	}
	.about-editorial {
		display: grid;
		grid-template-columns: minmax(0, 0.92fr) minmax(420px, 1.08fr);
		gap: 64px;
		align-items: center;
	}
	.about-copy {
		max-width: 620px;
	}
	.about-heading {
		font-family: var(--font-heading);
		font-size: clamp(2.7rem, 5.4vw, 5rem);
		font-weight: 300;
		line-height: 0.98;
		color: var(--off-white);
		margin-top: 18px;
	}
	.about-heading em {
		font-style: italic;
		color: var(--gold);
	}
	.story-text {
		display: grid;
		gap: 16px;
		max-width: 560px;
		margin-top: 34px;
	}
	.story-text p {
		font-family: var(--font-body);
		font-size: 0.86rem;
		font-weight: 300;
		line-height: 1.85;
		color: var(--light-grey);
	}
	.story-principles {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 18px;
		margin-top: 42px;
		padding-top: 26px;
		border-top: 1px solid rgba(245, 245, 240, 0.12);
	}
	.story-principles div {
		min-width: 0;
	}
	.story-principles span {
		font-family: var(--font-heading);
		font-size: 2.1rem;
		font-weight: 300;
		line-height: 1;
		color: rgba(201, 163, 71, 0.72);
	}
	.story-principles p {
		font-family: var(--font-body);
		font-size: 0.66rem;
		font-weight: 500;
		letter-spacing: 0.16em;
		line-height: 1.7;
		text-transform: uppercase;
		color: rgba(245, 245, 240, 0.78);
		margin-top: 10px;
	}
	.about-visual {
		position: relative;
		min-height: 610px;
	}
	.image-frame {
		overflow: hidden;
		background: var(--black);
	}
	.image-frame img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		transition: transform 0.8s ease;
	}
	.image-frame:hover img {
		transform: scale(1.04);
	}
	.main-image {
		position: absolute;
		top: 0;
		right: 0;
		width: 76%;
		height: 520px;
	}
	.detail-image {
		position: absolute;
		left: 0;
		bottom: 58px;
		width: 36%;
		height: 310px;
		border: 12px solid var(--dark-card);
	}
	.visual-note {
		position: absolute;
		right: 8%;
		bottom: 0;
		width: min(380px, 58%);
		padding: 22px 24px;
		background: rgba(10, 10, 10, 0.78);
		border-left: 1px solid var(--gold);
		backdrop-filter: blur(12px);
	}
	.visual-note span {
		font-family: var(--font-body);
		font-size: 0.58rem;
		font-weight: 500;
		letter-spacing: 0.24em;
		text-transform: uppercase;
		color: var(--gold);
	}
	.visual-note p {
		font-family: var(--font-heading);
		font-size: 1.35rem;
		font-weight: 300;
		line-height: 1.34;
		color: var(--off-white);
		margin-top: 10px;
	}

	@media (max-width: 980px) {
		.about {
			padding: 86px 28px 100px;
		}
		.about-editorial {
			grid-template-columns: 1fr;
			gap: 48px;
		}
		.about-copy {
			max-width: 760px;
		}
		.about-visual {
			min-height: 560px;
		}
	}
	@media (max-width: 700px) {
		.about {
			padding: 72px 20px 84px;
		}
		.about-shell {
			grid-template-columns: 1fr;
			gap: 34px;
		}
		.about-side {
			display: none;
		}
		.about-heading {
			font-size: clamp(2.6rem, 12vw, 4rem);
		}
		.story-principles {
			grid-template-columns: 1fr;
			gap: 20px;
		}
		.about-visual {
			min-height: auto;
			display: grid;
			gap: 12px;
		}
		.main-image,
		.detail-image,
		.visual-note {
			position: static;
			width: 100%;
		}
		.main-image {
			height: 360px;
		}
		.detail-image {
			height: 260px;
			border: 0;
		}
		.visual-note {
			width: 100%;
		}
	}
</style>
