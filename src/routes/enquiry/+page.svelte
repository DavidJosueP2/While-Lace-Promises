<script lang="ts">
	import { contact } from '$lib/contact';
	import Nav from '$lib/components/Nav.svelte';
	import Ornament from '$lib/components/Ornament.svelte';
	import Footer from '$lib/components/Footer.svelte';

	let scrollY = $state(0);

	$effect(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) entry.target.classList.add('visible');
				});
			},
			{ threshold: 0.1, rootMargin: '0px 0px -40px 0px' }
		);
		document.querySelectorAll('.fade-up').forEach((el) => observer.observe(el));
		return () => observer.disconnect();
	});
</script>

<svelte:head>
	<title>Enquiry - White Lace & Promises</title>
	<meta
		name="description"
		content="Reserve your date with White Lace & Promises. Complete our enquiry form and our team will be in touch within 24 business hours."
	/>
</svelte:head>

<svelte:window bind:scrollY />

<div class="enquiry-page">
	<Nav {scrollY} />

	<section class="enq-hero">
		<div class="watermark">Enquiry</div>
		<div class="enq-hero-content">
			<p class="section-label fade-up">RESERVE YOUR DATE</p>
			<h1 class="enq-title fade-up delay-1">Event <em>Enquiry</em></h1>
			<p class="enq-sub fade-up delay-2">
				Complete the form below and a member of our team will be in touch<br />
				within 24 business hours to discuss your styling vision and availability.
			</p>
			<Ornament />
		</div>
	</section>

	<section class="contact-cards fade-up">
		<div class="card">
			<span class="card-label">CALL US</span>
			<a href={contact.phoneHref} class="card-value">{contact.phoneLabel}</a>
		</div>
		<div class="card">
			<span class="card-label">EMAIL US</span>
			<a href={`mailto:${contact.email}`} class="card-value">{contact.email}</a>
		</div>
		<div class="card">
			<span class="card-label">VISIT US</span>
			<p class="card-value">{contact.addressLine1},<br />{contact.addressLine2}</p>
		</div>
	</section>

	<Ornament />

	<section class="enq-form-section">
		<form class="enq-form fade-up" onsubmit={(e) => e.preventDefault()}>
			<aside class="form-intro">
				<p class="form-eyebrow">BEGIN THE CONVERSATION</p>
				<h2>Your celebration, carefully understood.</h2>
				<p>
					Share the details that matter most and our team will use them to shape a thoughtful
					first response.
				</p>
				<div class="form-steps" aria-label="Enquiry sections">
					<span>Contact</span>
					<span>Event</span>
					<span>Styling</span>
				</div>
			</aside>

			<div class="form-fields">
				<fieldset class="form-panel">
					<legend><span>01</span> Your Details</legend>
					<div class="form-row">
						<div class="form-group">
							<label for="fullName">FULL NAME *</label>
							<input type="text" id="fullName" placeholder="Your full name" required />
						</div>
						<div class="form-group">
							<label for="email">EMAIL ADDRESS *</label>
							<input type="email" id="email" placeholder="your@email.com" required />
						</div>
					</div>
					<div class="form-row">
						<div class="form-group">
							<label for="phone">PHONE NUMBER *</label>
							<input type="tel" id="phone" placeholder="+61 000 000 000" required />
						</div>
						<div class="form-group">
							<label for="hearAbout">HOW DID YOU HEAR ABOUT US?</label>
							<select id="hearAbout">
								<option value="" disabled selected>Please select...</option>
								<option>Instagram</option>
								<option>Facebook</option>
								<option>Google Search</option>
								<option>Word of Mouth</option>
								<option>Wedding Expo</option>
								<option>Other</option>
							</select>
						</div>
					</div>
				</fieldset>

				<fieldset class="form-panel">
					<legend><span>02</span> Event Shape</legend>
					<div class="form-row">
						<div class="form-group">
							<label for="eventType">TYPE OF EVENT *</label>
							<select id="eventType" required>
								<option value="" disabled selected>Please select...</option>
								<option>Wedding</option>
								<option>Corporate Event</option>
								<option>Social Celebration</option>
								<option>Birthday Party</option>
								<option>Engagement Party</option>
								<option>Baby Shower</option>
								<option>Anniversary</option>
								<option>Other</option>
							</select>
						</div>
						<div class="form-group">
							<label for="guests">ESTIMATED GUEST COUNT *</label>
							<select id="guests" required>
								<option value="" disabled selected>Please select...</option>
								<option>1 - 50</option>
								<option>51 - 100</option>
								<option>101 - 150</option>
								<option>151 - 200</option>
								<option>201 - 300</option>
								<option>300+</option>
							</select>
						</div>
					</div>
					<div class="form-row">
						<div class="form-group">
							<label for="eventDate">PREFERRED EVENT DATE *</label>
							<input type="date" id="eventDate" required />
						</div>
						<div class="form-group">
							<label for="altDate">ALTERNATIVE DATE</label>
							<input type="date" id="altDate" />
						</div>
					</div>
					<div class="form-row">
						<div class="form-group">
							<label for="startTime">PREFERRED START TIME *</label>
							<input type="time" id="startTime" required />
						</div>
						<div class="form-group">
							<label for="endTime">ESTIMATED FINISH TIME</label>
							<input type="time" id="endTime" />
						</div>
					</div>
					<div class="form-row one-col">
						<div class="form-group">
							<label for="budget">APPROXIMATE BUDGET</label>
							<select id="budget">
								<option value="" disabled selected>Please select...</option>
								<option>Under $5,000</option>
								<option>$5,000 - $10,000</option>
								<option>$10,000 - $20,000</option>
								<option>$20,000 - $50,000</option>
								<option>$50,000+</option>
							</select>
						</div>
					</div>
				</fieldset>

				<fieldset class="form-panel services-group">
					<legend><span>03</span> Styling & Support</legend>
					<div class="checkbox-grid">
						{#each ['Catering', 'Floral Decorations', 'AV & Lighting', 'Themed Styling', 'Photography', 'Videography', 'MC Services', 'Dance Floor', 'Photo Booth', 'Bar Service'] as svc}
							<label class="checkbox-label">
								<input type="checkbox" value={svc} />
								<span class="custom-check" aria-hidden="true"></span>
								<span class="checkbox-text">{svc.toUpperCase()}</span>
							</label>
						{/each}
					</div>
				</fieldset>

				<fieldset class="form-panel">
					<legend><span>04</span> Notes & Vision</legend>
					<div class="form-group full">
						<label for="special">SPECIAL REQUESTS</label>
						<textarea
							id="special"
							rows="3"
							placeholder="Theme preferences, specific requirements..."
						></textarea>
					</div>
					<div class="form-group full">
						<label for="dietary">DIETARY REQUIREMENTS & ALLERGIES</label>
						<textarea
							id="dietary"
							rows="3"
							placeholder="Please list any dietary requirements, allergies or other considerations for your guests."
						></textarea>
					</div>
					<div class="form-group full">
						<label for="notes">ADDITIONAL NOTES</label>
						<textarea
							id="notes"
							rows="5"
							placeholder="Share your vision or any questions you have for our team..."></textarea>
					</div>
				</fieldset>

				<div class="form-submit">
					<p class="form-note">* Required fields. We'll respond within 24 business hours.</p>
					<button type="submit" class="submit-btn">SUBMIT ENQUIRY</button>
				</div>
			</div>
		</form>
	</section>

	<Footer />
</div>

<style>
	.enquiry-page {
		background: #f1e7cf;
		min-height: 100vh;
	}

	.enquiry-page :global(.nav) {
		background: rgba(10, 10, 10, 0.98);
		backdrop-filter: blur(12px);
	}
	.enquiry-page :global(.nav.solid) {
		background: rgba(10, 10, 10, 0.98);
	}
	.enquiry-page :global(.nav-link) {
		color: rgba(245, 245, 240, 0.72);
	}
	.enquiry-page :global(.nav-link:hover),
	.enquiry-page :global(.nav-logo) {
		color: var(--gold);
	}
	.enquiry-page :global(.nav-enquire) {
		background: var(--gold);
		color: var(--black);
		border-color: var(--gold);
	}
	.enquiry-page :global(.nav-enquire:hover) {
		background: var(--gold-hover);
		border-color: var(--gold-hover);
	}
	.enquiry-page :global(.bar) {
		background: var(--off-white);
	}
	.enquiry-page :global(.ornament) {
		padding: 32px 0;
	}
	.enquiry-page :global(.section-label) {
		color: var(--gold);
	}
	.enquiry-page :global(.footer) {
		background: var(--black);
	}

	.enq-hero {
		position: relative;
		padding: 185px 48px 92px;
		text-align: center;
		overflow: hidden;
	}
	.watermark {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		font-family: var(--font-heading);
		font-size: clamp(6rem, 14vw, 12rem);
		font-weight: 300;
		font-style: italic;
		color: rgba(201, 163, 71, 0.07);
		white-space: nowrap;
		pointer-events: none;
		user-select: none;
	}
	.enq-hero-content {
		position: relative;
		z-index: 2;
	}
	.enq-title {
		font-family: var(--font-heading);
		font-size: clamp(2.4rem, 6vw, 4.5rem);
		font-weight: 300;
		line-height: 1.15;
		color: #2a2218;
		margin-top: 16px;
	}
	.enq-title em {
		font-style: italic;
		color: var(--gold);
	}
	.enq-sub {
		font-family: var(--font-body);
		font-size: 0.86rem;
		font-weight: 300;
		line-height: 1.8;
		color: #6b6358;
		margin-top: 12px;
	}

	.contact-cards {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 0;
		max-width: 1110px;
		margin: 0 auto;
		padding: 0 48px;
	}
	.card {
		background: #e8d9b4;
		padding: 34px 40px;
		display: flex;
		flex-direction: column;
		gap: 8px;
		min-height: 148px;
		justify-content: center;
	}
	.card + .card {
		border-left: 1px solid rgba(245, 242, 234, 0.65);
	}
	.card-label {
		font-family: var(--font-body);
		font-size: 0.6rem;
		font-weight: 500;
		letter-spacing: 0.25em;
		color: var(--gold);
	}
	.card-value {
		font-family: var(--font-heading);
		font-size: 1.05rem;
		font-weight: 400;
		color: #2a2218;
		line-height: 1.5;
		text-decoration: none;
		transition: color 0.3s;
	}
	a.card-value:hover {
		color: var(--gold);
	}

	.enq-form-section {
		max-width: 1180px;
		margin: 0 auto;
		padding: 18px 48px 86px;
	}
	.enq-form {
		display: grid;
		grid-template-columns: minmax(260px, 0.36fr) minmax(0, 1fr);
		gap: 44px;
		align-items: start;
	}
	.form-intro {
		position: sticky;
		top: 110px;
		padding: 36px 0 32px;
		border-top: 1px solid rgba(201, 163, 71, 0.46);
		border-bottom: 1px solid rgba(201, 163, 71, 0.2);
	}
	.form-eyebrow,
	.form-panel legend,
	.form-group label {
		font-family: var(--font-body);
		font-size: 0.6rem;
		font-weight: 500;
		letter-spacing: 0.24em;
		color: var(--gold);
		text-transform: uppercase;
	}
	.form-intro h2 {
		font-family: var(--font-heading);
		font-size: clamp(2.2rem, 4vw, 3.6rem);
		font-weight: 300;
		line-height: 1.02;
		color: #2a2218;
		margin-top: 18px;
	}
	.form-intro p:not(.form-eyebrow) {
		font-family: var(--font-body);
		font-size: 0.8rem;
		font-weight: 300;
		line-height: 1.8;
		color: #6b6358;
		margin-top: 18px;
	}
	.form-steps {
		display: grid;
		gap: 12px;
		margin-top: 34px;
	}
	.form-steps span {
		font-family: var(--font-body);
		font-size: 0.62rem;
		font-weight: 500;
		letter-spacing: 0.2em;
		text-transform: uppercase;
		color: #2a2218;
		padding-left: 18px;
		border-left: 1px solid var(--gold);
	}
	.form-fields {
		display: grid;
		gap: 22px;
	}
	.form-panel {
		position: relative;
		border: 1px solid rgba(201, 163, 71, 0.2);
		background: rgba(245, 242, 234, 0.34);
		padding: 30px;
	}
	.form-panel::before {
		content: '';
		position: absolute;
		inset: 10px;
		border: 1px solid rgba(245, 242, 234, 0.42);
		pointer-events: none;
	}
	.form-panel legend {
		float: left;
		display: flex;
		align-items: center;
		gap: 12px;
		width: 100%;
		margin-bottom: 24px;
		color: #2a2218;
	}
	.form-panel legend span {
		font-family: var(--font-heading);
		font-size: 2rem;
		font-weight: 300;
		line-height: 1;
		color: rgba(201, 163, 71, 0.82);
		letter-spacing: 0;
	}
	.form-panel legend + * {
		clear: both;
	}
	.form-row {
		display: grid;
		grid-template-columns: repeat(2, minmax(0, 1fr));
		gap: 24px;
		margin-bottom: 24px;
	}
	.form-row:last-child,
	.form-group.full:last-child {
		margin-bottom: 0;
	}
	.form-row.one-col {
		grid-template-columns: minmax(0, 1fr);
	}
	.form-group {
		display: flex;
		flex-direction: column;
		gap: 9px;
	}
	.form-group.full {
		margin-bottom: 24px;
	}
	.form-group input,
	.form-group select,
	.form-group textarea {
		width: 100%;
		font-family: var(--font-heading);
		font-size: 1.06rem;
		font-weight: 400;
		color: #2a2218;
		background: rgba(241, 231, 207, 0.58);
		border: 1px solid rgba(101, 88, 64, 0.18);
		padding: 14px 16px;
		outline: none;
		transition:
			border-color 0.28s ease,
			background 0.28s ease,
			box-shadow 0.28s ease;
		appearance: auto;
	}
	.form-group textarea {
		resize: vertical;
		min-height: 108px;
		font-family: var(--font-body);
		font-size: 0.86rem;
		line-height: 1.7;
	}
	.form-group input:focus,
	.form-group select:focus,
	.form-group textarea:focus {
		background: rgba(245, 242, 234, 0.78);
		border-color: rgba(201, 163, 71, 0.72);
		box-shadow: 0 0 0 4px rgba(201, 163, 71, 0.1);
	}
	.form-group input::placeholder,
	.form-group textarea::placeholder {
		color: rgba(82, 72, 52, 0.45);
		font-style: italic;
	}

	.services-group {
		padding-bottom: 34px;
	}
	.checkbox-grid {
		display: grid;
		grid-template-columns: repeat(2, minmax(0, 1fr));
		gap: 12px;
	}
	.checkbox-label {
		position: relative;
		display: flex;
		align-items: center;
		gap: 10px;
		min-height: 44px;
		padding: 12px 14px;
		cursor: pointer;
		background: rgba(241, 231, 207, 0.42);
		border: 1px solid rgba(101, 88, 64, 0.14);
		transition:
			border-color 0.25s ease,
			background 0.25s ease,
			transform 0.25s ease;
	}
	.checkbox-label:hover {
		border-color: rgba(201, 163, 71, 0.62);
		background: rgba(245, 242, 234, 0.62);
		transform: translateY(-1px);
	}
	.checkbox-label input[type='checkbox'] {
		position: absolute;
		width: 1px;
		height: 1px;
		opacity: 0;
		pointer-events: none;
	}
	.custom-check {
		position: relative;
		width: 16px;
		height: 16px;
		flex: 0 0 16px;
		border: 1px solid rgba(42, 34, 24, 0.45);
		background: rgba(245, 242, 234, 0.4);
		transition:
			background 0.25s ease,
			border-color 0.25s ease,
			box-shadow 0.25s ease;
	}
	.custom-check::after {
		content: '';
		position: absolute;
		left: 4px;
		top: 1px;
		width: 5px;
		height: 9px;
		border-right: 1.5px solid #2a2218;
		border-bottom: 1.5px solid #2a2218;
		opacity: 0;
		transform: rotate(40deg) scale(0.8);
		transition:
			opacity 0.2s ease,
			transform 0.2s ease;
	}
	.checkbox-label input[type='checkbox']:checked + .custom-check {
		border-color: var(--gold);
		background: var(--gold);
		box-shadow: 0 0 0 3px rgba(201, 163, 71, 0.14);
	}
	.checkbox-label input[type='checkbox']:checked + .custom-check::after {
		opacity: 1;
		transform: rotate(40deg) scale(1);
	}
	.checkbox-label input[type='checkbox']:focus-visible + .custom-check {
		outline: 1px solid var(--gold);
		outline-offset: 3px;
	}
	.checkbox-text {
		font-family: var(--font-body);
		font-size: 0.64rem;
		font-weight: 500;
		letter-spacing: 0.14em;
		color: #4f4739;
	}

	.form-submit {
		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 24px;
		padding: 26px 0 0;
		border-top: 1px solid rgba(201, 163, 71, 0.28);
	}
	.submit-btn {
		font-family: var(--font-body);
		font-size: 0.66rem;
		font-weight: 500;
		letter-spacing: 0.25em;
		background: #2a2218;
		color: #f5f2ea;
		border: 1px solid #2a2218;
		padding: 18px 54px;
		cursor: pointer;
		transition:
			background 0.3s ease,
			border-color 0.3s ease,
			color 0.3s ease;
	}
	.submit-btn:hover {
		background: var(--gold);
		border-color: var(--gold);
		color: #2a2218;
	}
	.form-note {
		font-family: var(--font-body);
		font-size: 0.72rem;
		font-weight: 300;
		color: #8f836e;
	}

	@media (max-width: 900px) {
		.enq-form {
			grid-template-columns: 1fr;
			gap: 30px;
		}
		.form-intro {
			position: static;
			padding: 28px 0;
		}
		.form-steps {
			grid-template-columns: repeat(3, 1fr);
		}
	}
	@media (max-width: 768px) {
		.enq-hero {
			padding: 132px 20px 44px;
		}
		.enq-sub br {
			display: none;
		}
		.contact-cards {
			grid-template-columns: 1fr;
			padding: 0 20px;
		}
		.card {
			padding: 26px 24px;
			min-height: auto;
		}
		.card + .card {
			border-left: none;
			border-top: 1px solid rgba(245, 242, 234, 0.65);
		}
		.enq-form-section {
			padding: 20px 20px 48px;
		}
		.form-panel {
			padding: 24px 20px;
		}
		.form-row,
		.checkbox-grid {
			grid-template-columns: 1fr;
			gap: 18px;
		}
		.form-steps {
			grid-template-columns: 1fr;
		}
		.form-submit {
			align-items: stretch;
			flex-direction: column-reverse;
		}
		.submit-btn {
			width: 100%;
		}
	}
</style>
