<script lang="ts">
	import { contact } from '$lib/contact';
</script>

<footer class="footer">
	<div class="footer-gold-line"></div>
	<div class="footer-inner">
		<div class="footer-col brand">
			<a href="/" class="footer-logo-mark" aria-label="White Lace & Promises home">
				<img src="/imgs/logo-removebg.png" alt="" aria-hidden="true" />
				<span>WHITE LACE & PROMISES</span>
			</a>
			<p class="footer-tagline">
				Brisbane based wedding and event stylist, event planning, consulting, designer and
				execution specialist for luxuriously themed and styled events.
			</p>
			<p class="footer-location">{contact.addressFull}</p>
		</div>
		<div class="footer-col">
			<h4 class="footer-heading">Explore</h4>
			<a href="/about" class="footer-link">About Us</a>
			<a href="/events" class="footer-link">Events We Style</a>
			<a href="/gallery" class="footer-link">Gallery</a>
			<a href="/#contact" class="footer-link">Contact Us</a>
		</div>
		<div class="footer-col">
			<h4 class="footer-heading">Connect</h4>
			<a href={contact.instagramHref} target="_blank" rel="noopener noreferrer" class="footer-link"
				>Instagram</a
			>
			<a href={contact.whatsappHref} target="_blank" rel="noopener noreferrer" class="footer-link"
				>WhatsApp</a
			>
			<a href={`mailto:${contact.email}`} class="footer-link">{contact.email}</a>
			<a href={contact.phoneHref} class="footer-link">{contact.phoneLabel}</a>
		</div>
	</div>
	<div class="footer-bottom">
		<p>&copy; {new Date().getFullYear()} White Lace & Promises. All rights reserved.</p>
	</div>
</footer>

<style>
	.footer {
		background: var(--black);
	}
	.footer-gold-line {
		height: 1px;
		background: linear-gradient(to right, transparent, var(--gold), transparent);
	}
	.footer-inner {
		display: grid;
		grid-template-columns: 1.5fr 1fr 1fr;
		gap: 48px;
		max-width: 1200px;
		margin: 0 auto;
		padding: 64px 48px 48px;
	}
	.footer-logo-mark {
		position: relative;
		display: flex;
		align-items: center;
		gap: 16px;
		width: fit-content;
		margin-bottom: 20px;
		padding-bottom: 18px;
		border-bottom: 1px solid rgba(201, 163, 71, 0.34);
		transition: border-color 0.3s ease;
	}
	.footer-logo-mark:hover {
		border-color: rgba(201, 163, 71, 0.55);
	}
	.footer-logo-mark img {
		width: 74px;
		height: 58px;
		object-fit: contain;
		opacity: 0.48;
		filter: invert(1) grayscale(1);
	}
	.footer-logo-mark span {
		max-width: 220px;
		font-family: var(--font-body);
		font-size: 0.72rem;
		font-weight: 400;
		letter-spacing: 0.28em;
		line-height: 1.8;
		color: var(--gold);
	}
	.footer-tagline {
		font-family: var(--font-body);
		font-size: 0.78rem;
		font-weight: 300;
		color: var(--grey);
		line-height: 1.6;
	}
	.footer-location {
		font-family: var(--font-body);
		font-size: 0.72rem;
		font-weight: 300;
		color: var(--grey);
		margin-top: 8px;
	}
	.footer-heading {
		font-family: var(--font-body);
		font-size: 0.65rem;
		font-weight: 500;
		letter-spacing: 0.2em;
		text-transform: uppercase;
		color: var(--off-white);
		margin-bottom: 20px;
	}
	.footer-col {
		display: flex;
		flex-direction: column;
		gap: 10px;
	}
	.footer-link {
		font-family: var(--font-body);
		font-size: 0.78rem;
		font-weight: 300;
		color: var(--grey);
		transition: color 0.3s;
	}
	.footer-link:hover {
		color: var(--gold);
	}
	.footer-bottom {
		border-top: 1px solid rgba(153, 153, 153, 0.15);
		padding: 24px 48px;
		text-align: center;
	}
	.footer-bottom p {
		font-family: var(--font-body);
		font-size: 0.7rem;
		font-weight: 300;
		color: rgba(153, 153, 153, 0.6);
	}

	@media (max-width: 768px) {
		.footer-inner {
			grid-template-columns: 1fr;
			gap: 36px;
			padding: 48px 20px 36px;
		}
		.footer-bottom {
			padding: 20px;
		}
	}
</style>
