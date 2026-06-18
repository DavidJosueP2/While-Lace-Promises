<script lang="ts">
	let audio: HTMLAudioElement | undefined = $state();
	let started = $state(false);
	let muted = $state(false);

	const MAX_VOLUME = 0.10;
	const FADE_MS = 1200;
	const PLAY_DURATION = 35000; // 35 seconds then fade out

	function fadeVolume(target: number, onDone?: () => void) {
		if (!audio) return;
		const steps = 24;
		const stepTime = FADE_MS / steps;
		const diff = (target - audio.volume) / steps;
		let i = 0;
		const interval = setInterval(() => {
			if (!audio || ++i >= steps) {
				if (audio) audio.volume = Math.max(0, Math.min(1, target));
				clearInterval(interval);
				if (target === 0 && audio) audio.pause();
				onDone?.();
				return;
			}
			audio.volume = Math.max(0, Math.min(1, audio.volume + diff));
		}, stepTime);
	}

	function startPlayback() {
		if (started || !audio) return;
		audio.volume = 0;
		audio.play().then(() => {
			started = true;
			fadeVolume(MAX_VOLUME);
			// Auto fade-out after duration
			setTimeout(() => {
				if (!muted && audio && !audio.paused) {
					fadeVolume(0, () => { muted = true; });
				}
			}, PLAY_DURATION);
		}).catch(() => {});
	}

	function toggle() {
		if (!audio) return;
		if (!started) { startPlayback(); return; }
		if (muted) {
			audio.play();
			fadeVolume(MAX_VOLUME);
			muted = false;
		} else {
			fadeVolume(0);
			muted = true;
		}
	}

	$effect(() => {
		const handler = () => startPlayback();
		window.addEventListener('click', handler, { once: true });
		window.addEventListener('scroll', handler, { once: true });

		const visHandler = () => {
			if (!audio || !started) return;
			if (document.hidden) {
				fadeVolume(0);
			} else if (!muted) {
				audio.play();
				fadeVolume(MAX_VOLUME);
			}
		};
		document.addEventListener('visibilitychange', visHandler);

		return () => {
			window.removeEventListener('click', handler);
			window.removeEventListener('scroll', handler);
			document.removeEventListener('visibilitychange', visHandler);
		};
	});
</script>

<audio bind:this={audio} src="/music/the_mountain-wedding-522480.mp3" loop preload="auto"></audio>

<button class="music-toggle" onclick={toggle} aria-label={muted || !started ? 'Play music' : 'Mute music'}>
	{#if muted || !started}
		<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
			<path d="M11 5L6 9H2v6h4l5 4V5z" />
			<line x1="23" y1="9" x2="17" y2="15" />
			<line x1="17" y1="9" x2="23" y2="15" />
		</svg>
	{:else}
		<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
			<path d="M11 5L6 9H2v6h4l5 4V5z" />
			<path d="M15.54 8.46a5 5 0 010 7.07" />
			<path d="M19.07 4.93a10 10 0 010 14.14" />
		</svg>
	{/if}
</button>

<style>
	.music-toggle {
		position: fixed;
		bottom: 28px;
		right: 28px;
		z-index: 90;
		width: 40px;
		height: 40px;
		border-radius: 50%;
		border: 1px solid rgba(201, 163, 71, 0.4);
		background: rgba(10, 10, 10, 0.7);
		backdrop-filter: blur(8px);
		color: var(--gold);
		cursor: pointer;
		display: flex;
		align-items: center;
		justify-content: center;
		padding: 8px;
		transition: border-color 0.3s, background 0.3s;
	}
	.music-toggle:hover {
		border-color: var(--gold);
		background: rgba(10, 10, 10, 0.9);
	}
	.music-toggle svg {
		width: 18px;
		height: 18px;
	}
</style>
