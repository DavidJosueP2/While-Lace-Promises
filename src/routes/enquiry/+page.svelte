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
	<title>Enquiry — White Lace & Promises</title>
	<meta
		name="description"
		content="Reserve your date with White Lace & Promises in Australia. Complete our enquiry form and our team will be in touch within 24 business hours."
	/>
</svelte:head>

<svelte:window bind:scrollY />

<div class="enquiry-page">
	<Nav {scrollY} />

	<!-- Hero Header -->
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

	<!-- Contact Cards -->
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

	<!-- Ornament -->
	<Ornament />

	<!-- Form -->
	<section class="enq-form-section">
		<form class="enq-form fade-up" onsubmit={(e) => e.preventDefault()}>
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
					<label for="guests">ESTIMATED GUEST COUNT *</label>
					<select id="guests" required>
						<option value="" disabled selected>Please select...</option>
						<option>1 – 50</option>
						<option>51 – 100</option>
						<option>101 – 150</option>
						<option>151 – 200</option>
						<option>201 – 300</option>
						<option>300+</option>
					</select>
				</div>
				<div class="form-group">
					<label for="budget">APPROXIMATE BUDGET</label>
					<select id="budget">
						<option value="" disabled selected>Please select...</option>
						<option>Under $5,000</option>
						<option>$5,000 – $10,000</option>
						<option>$10,000 – $20,000</option>
						<option>$20,000 – $50,000</option>
						<option>$50,000+</option>
					</select>
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

			<!-- Services Checkboxes -->
			<fieldset class="form-group full services-group">
				<legend>ADDITIONAL SERVICES OF INTEREST</legend>
				<div class="checkbox-grid">
					{#each ['Catering', 'Floral Decorations', 'AV & Lighting', 'Themed Styling', 'Photography', 'Videography', 'MC Services', 'Dance Floor', 'Photo Booth', 'Bar Service'] as svc}
						<label class="checkbox-label">
							<input type="checkbox" value={svc} />
							<span>{svc.toUpperCase()}</span>
						</label>
					{/each}
				</div>
			</fieldset>

			<!-- Dietary -->
			<div class="form-group full">
				<label for="dietary">DIETARY REQUIREMENTS & ALLERGIES</label>
				<textarea
					id="dietary"
					rows="3"
					placeholder="Please list any dietary requirements, allergies or other considerations for your guests."
				></textarea>
			</div>

			<div class="form-row">
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
				<div class="form-group">
					<label for="special">SPECIAL REQUESTS</label>
					<textarea id="special" rows="3" placeholder="Theme preferences, specific requirements..."
					></textarea>
				</div>
			</div>

			<div class="form-group full">
				<label for="notes">ADDITIONAL NOTES</label>
				<textarea
					id="notes"
					rows="5"
					placeholder="Share your vision or any questions you have for our team..."></textarea>
			</div>

			<div class="form-submit">
				<button type="submit" class="submit-btn">SUBMIT ENQUIRY</button>
				<p class="form-note">
					* Required fields &nbsp;&middot;&nbsp; We'll respond within 24 business hours.
				</p>
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

	/* Enquiry uses the same dark top bar treatment as the reference. */
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
	.enquiry-page :global(.nav-link:hover) {
		color: var(--gold);
	}
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

	/* Override ornament for light bg */
	.enquiry-page :global(.ornament) {
		padding: 32px 0;
	}

	/* Override section-label */
	.enquiry-page :global(.section-label) {
		color: var(--gold);
	}

	/* Override footer for dark on light page */
	.enquiry-page :global(.footer) {
		background: var(--black);
	}

	/* Hero */
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

	/* Contact Cards */
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

	/* Form */
	.enq-form-section {
		max-width: 1110px;
		margin: 0 auto;
		padding: 20px 48px 72px;
	}
	.form-row {
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 32px;
		margin-bottom: 32px;
	}
	.form-group {
		display: flex;
		flex-direction: column;
		gap: 8px;
	}
	.form-group.full {
		margin-bottom: 32px;
	}
	.form-group label,
	.form-group legend {
		font-family: var(--font-body);
		font-size: 0.6rem;
		font-weight: 500;
		letter-spacing: 0.25em;
		color: var(--gold);
		text-transform: uppercase;
	}
	.services-group {
		border: 0;
		padding: 0;
	}
	.form-group input,
	.form-group select,
	.form-group textarea {
		font-family: var(--font-heading);
		font-size: 1rem;
		font-weight: 400;
		color: #2a2218;
		background: transparent;
		border: none;
		border-bottom: 1px solid #ccc5b5;
		padding: 10px 0;
		outline: none;
		transition: border-color 0.3s;
		appearance: auto;
	}
	.form-group textarea {
		border: 1px solid #ccc5b5;
		padding: 14px;
		resize: vertical;
		font-family: var(--font-body);
		font-size: 0.85rem;
	}
	.form-group input:focus,
	.form-group select:focus,
	.form-group textarea:focus {
		border-color: var(--gold);
	}
	.form-group input::placeholder,
	.form-group textarea::placeholder {
		color: #b5ae9f;
		font-style: italic;
	}

	/* Checkboxes */
	.checkbox-grid {
		display: flex;
		flex-wrap: wrap;
		gap: 8px 24px;
		margin-top: 4px;
	}
	.checkbox-label {
		display: flex;
		align-items: center;
		gap: 6px;
		cursor: pointer;
	}
	.checkbox-label input[type='checkbox'] {
		width: 14px;
		height: 14px;
		accent-color: var(--gold);
		cursor: pointer;
	}
	.checkbox-label span {
		font-family: var(--font-body);
		font-size: 0.65rem;
		font-weight: 400;
		letter-spacing: 0.15em;
		color: #5a5347;
	}

	/* Submit */
	.form-submit {
		text-align: center;
		margin-top: 64px;
		padding-top: 64px;
		border-top: 1px solid rgba(201, 163, 71, 0.18);
	}
	.submit-btn {
		font-family: var(--font-body);
		font-size: 0.65rem;
		font-weight: 500;
		letter-spacing: 0.25em;
		background: #2a2218;
		color: #f5f2ea;
		border: none;
		padding: 18px 56px;
		cursor: pointer;
		transition: background 0.3s;
	}
	.submit-btn:hover {
		background: var(--gold);
		color: #2a2218;
	}
	.form-note {
		font-family: var(--font-body);
		font-size: 0.7rem;
		font-weight: 300;
		color: #a09888;
		margin-top: 16px;
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
			padding: 20px 20px 40px;
		}
		.form-row {
			grid-template-columns: 1fr;
			gap: 24px;
		}
		.form-submit {
			margin-top: 44px;
			padding-top: 44px;
		}
	}
</style>
