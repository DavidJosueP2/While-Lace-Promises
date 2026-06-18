<script lang="ts">
	import { contact } from '$lib/contact';
</script>

<section id="contact" class="contact">
	<div class="contact-inner">
		<h2 class="contact-heading fade-up">
			Begin Your<br /><em>Promise</em>
		</h2>
		<p class="body-text contact-sub fade-up delay-1">
			Ready to create something extraordinary? Our team is here to bring<br />
			your vision to life - every detail, perfectly placed.
		</p>
		<div class="contact-btns fade-up delay-2">
			<a href={contact.whatsappHref} target="_blank" rel="noopener noreferrer" class="btn-wa">
				<svg class="wa-icon" viewBox="0 0 24 24" fill="currentColor" width="16" height="16">
					<path
						d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"
					/>
				</svg>
				CHAT ON WHATSAPP
			</a>
			<a href="/enquiry" class="btn-enquiry">SEND AN ENQUIRY</a>
		</div>
	</div>
</section>

<style>
	.contact {
		background: var(--dark);
		padding: 100px 48px 110px;
		text-align: center;
	}
	.contact-inner {
		max-width: 900px;
		margin: 0 auto;
	}
	.contact-heading {
		font-family: var(--font-heading);
		font-size: clamp(3.4rem, 8vw, 6.5rem);
		font-weight: 300;
		line-height: 1;
		color: var(--off-white);
		margin-bottom: 28px;
	}
	.contact-heading em {
		font-style: italic;
		color: var(--gold);
	}
	.contact-sub {
		max-width: 500px;
		margin: 0 auto;
	}
	.contact-btns {
		display: flex;
		gap: 16px;
		justify-content: center;
		margin-top: 42px;
		flex-wrap: wrap;
	}
	.btn-wa,
	.btn-enquiry {
		font-family: var(--font-body);
		font-size: 0.6rem;
		font-weight: 500;
		letter-spacing: 0.2em;
		padding: 14px 32px;
		cursor: pointer;
		transition: all 0.3s ease;
		display: inline-flex;
		align-items: center;
		gap: 8px;
		text-decoration: none;
	}
	.btn-wa {
		background: var(--gold);
		color: var(--black);
		border: 1px solid var(--gold);
	}
	.btn-wa:hover {
		background: var(--gold-hover);
	}
	.wa-icon {
		flex-shrink: 0;
	}
	.btn-enquiry {
		background: transparent;
		color: var(--off-white);
		border: 1px solid rgba(245, 245, 240, 0.3);
	}
	.btn-enquiry:hover {
		border-color: var(--gold);
		color: var(--gold);
	}

	@media (max-width: 768px) {
		.contact {
			padding: 72px 20px 84px;
		}
		.contact-heading {
			font-size: clamp(3rem, 15vw, 4.6rem);
		}
		.contact-sub :global(br) {
			display: none;
		}
		.contact-btns {
			flex-direction: column;
			align-items: center;
		}
		.btn-wa,
		.btn-enquiry {
			width: 240px;
			justify-content: center;
		}
	}
</style>
