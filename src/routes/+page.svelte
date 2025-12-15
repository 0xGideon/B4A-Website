<script lang="ts">
	import about from '$lib/assets/images/about.webp';
	import banner from '$lib/assets/images/banner.svg';
	import logo from '$lib/assets/images/logo.svg';
	const navItems = [
		{ id: 'home', label: 'Home' },
		{ id: 'about', label: 'About Us' },
		{ id: 'testimonials', label: 'Testimonials' },
		{ id: 'contact', label: 'Contact Us' }
	];

	const testimonials = [
		`B4A's development expertise in crafting our decentralized application was outstanding. Their attention to detail and deep knowledge of blockchain technology ensured a seamless and secure user experience. We highly recommend B4A for any Web3 project.`,
		`Partnering with B4A for the development of our smart contracts was a game changer. Their meticulous approach to security and efficiency ensured our contracts were robust and reliable. B4A's commitment to excellence shines through in every line of code.`,
		`B4A's business development strategies have been pivotal in expanding our Web3 project. Their market insights and strategic partnerships helped us reach new heights. We are grateful for B4A's expertise and dedication to our success.`
	];

	const mailRecipient = 'info@b4a.com';
	const phoneNumber = '+2349036534493';

	let mobileOpen = false;
	let activeNav = 'home';

	const scrollToSection = (id: string) => {
		const el = document.getElementById(id);
		if (el) {
			el.scrollIntoView({ behavior: 'smooth', block: 'start' });
		}
	};

	const handleNav = (id: string, event?: Event) => {
		event?.preventDefault();
		activeNav = id;
		scrollToSection(id);
		if (mobileOpen) mobileOpen = false;
	};

	const handleSubmit = (event: SubmitEvent) => {
		event.preventDefault();
		const form = event.currentTarget as HTMLFormElement;
		const formData = new FormData(form);
		const name = (formData.get('name') as string)?.trim() || 'Website Contact';
		const message = (formData.get('message') as string)?.trim() || '';
		const subject = encodeURIComponent(name);
		const body = encodeURIComponent(message);
		window.location.href = `mailto:${mailRecipient}?subject=${subject}&body=${body}`;
	};
</script>

<svelte:head>
	<title>Web3: The B4A Synergy | Blockchain Web3 Advisory</title>
	<meta
		name="description"
		content="B4A guides Web3 teams with crypto-native strategy, product design, marketing, and technical consulting to navigate the new frontier with confidence."
	/>
	<meta
		name="keywords"
		content="Web3 strategy, blockchain consulting, crypto marketing, tokenization, smart contract advisory, product design"
	/>
	<meta name="robots" content="index, follow" />
	<meta property="og:type" content="website" />
	<meta property="og:title" content="Web3: The B4A Synergy" />
	<meta
		property="og:description"
		content="Blueprints for success in the Web3 frontier from the team at B4A."
	/>
	<meta property="og:image" content={banner} />
	<meta property="og:url" content="https://b4a.com/" />
	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content="Web3: The B4A Synergy" />
	<meta
		name="twitter:description"
		content="Blueprints for success in the Web3 frontier from the team at B4A."
	/>
	<meta name="twitter:image" content={banner} />
	<meta name="theme-color" content="#00aeef" />
	<meta name="format-detection" content="telephone=yes" />
	<link rel="canonical" href="https://b4a.com/" />
	<script type="application/ld+json">
		{JSON.stringify({
			'@context': 'https://schema.org',
			'@type': 'Organization',
			name: 'B4A',
			url: 'https://b4a.com/',
			logo: logo,
			contactPoint: [
				{
					'@type': 'ContactPoint',
					telephone: '+2349036534493',
					contactType: 'customer support',
					availableLanguage: ['en']
				}
			],
			sameAs: ['https://x.com', 'https://t.me']
		})}
	</script>
</svelte:head>

<a
	href="#main-content"
	class="sr-only focus:not-sr-only focus:absolute focus:top-4 focus:left-4 focus:z-50 focus:px-4 focus:py-2 focus:bg-white focus:text-gray-900 focus:shadow-lg"
>
	Skip to main content
</a>

<header id="home" class="relative isolate w-full overflow-hidden text-white">
	<div class="absolute inset-0 bg-[#131316]">
		<img
			src={banner}
			alt="Web3 network background"
			width="1980"
			height="756"
			class="h-full w-full max-w-6xl mx-auto object-cover object-left sm:object-center"
			loading="eager"
			fetchpriority="high"
		/>
		<div class="absolute inset-0 bg-black/5"></div>
	</div>
	<div class="relative mx-auto flex max-w-6xl flex-col gap-8 px-5 pb-16 pt-6 md:px-8 md:pb-24">
		<nav class="flex items-center justify-between flex-1" aria-label="Main navigation">
			<div class="flex flex-1 items-center gap-4 justify-between">
				<a href="#home" class="inline-flex items-center" on:click|preventDefault={() => handleNav('home')}>
					<img src={logo} alt="B4A logo" width="140" height="112" class="h-20 w-auto" loading="eager" />
				</a>
				<button
					id="menu-toggle"
					class="flex h-9 w-9 items-center justify-center md:hidden"
					aria-label="Toggle navigation"
					aria-expanded={mobileOpen}
					aria-controls="mobile-menu"
					type="button"
					on:click={() => (mobileOpen = !mobileOpen)}
				>
					<span class="sr-only">Open menu</span>
					<svg width="60" height="60" viewBox="0 0 60 60" fill="none" xmlns="http://www.w3.org/2000/svg">
						<path d="M7.5 45V40H52.5V45H7.5ZM7.5 32.5V27.5H52.5V32.5H7.5ZM7.5 20V15H52.5V20H7.5Z" fill="white" />
					</svg>
				</button>
			</div>
			<div class="hidden items-stretch overflow-hidden rounded shadow-lg md:flex">
				{#each navItems as item}
					<a
						href={`#${item.id}`}
						data-nav="desktop"
						on:click={(event) => handleNav(item.id, event)}
						class={`nav-link nav-link-desktop px-6 py-3 text-sm font-semibold transition duration-300 hover:bg-primary-light hover:text-white ${
							activeNav === item.id ? 'bg-primary text-white' : 'bg-white text-gray-900'
						}`}
						aria-current={activeNav === item.id ? 'page' : undefined}
					>
						{item.label}
					</a>
				{/each}
			</div>
		</nav>

		<div
			id="mobile-overlay"
			class={`fixed inset-0 z-30 bg-black/50 transition md:hidden ${
				mobileOpen ? 'opacity-100' : 'pointer-events-none opacity-0'
			}`}
			aria-hidden={!mobileOpen}
			on:click={() => (mobileOpen = false)}
		></div>

		<div
			id="mobile-menu"
			class={`pointer-events-none fixed top-0 right-0 z-40 flex h-full w-64 max-w-[80vw] flex-col gap-1 border-l border-white/20 bg-secondary/95 px-6 pb-10 pt-16 backdrop-blur transition-all duration-300 ease-in-out md:hidden shadow-2xl ${
				mobileOpen ? 'translate-x-0 opacity-100 pointer-events-auto' : 'translate-x-full opacity-0'
			}`}
			role="menu"
			aria-hidden={!mobileOpen}
		>
			<div class="flex justify-end pb-2">
				<button
					id="menu-close"
					aria-label="Close navigation"
					class="inline-flex h-9 w-9 items-center justify-center rounded border border-white/20 text-white hover:border-white/40"
					type="button"
					on:click={() => (mobileOpen = false)}
				>
					<svg
						class="h-5 w-5"
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"
						aria-hidden="true"
					>
						<path d="M18 6 6 18" />
						<path d="m6 6 12 12" />
					</svg>
				</button>
			</div>

			{#each navItems as item}
				<a
					href={`#${item.id}`}
					data-nav="mobile"
					class={`nav-link nav-link-mobile rounded px-4 py-3 text-sm font-semibold text-white hover:bg-white/10 ${
						activeNav === item.id ? 'bg-white/10' : ''
					}`}
					role="menuitem"
					aria-current={activeNav === item.id ? 'page' : undefined}
					on:click={(event) => handleNav(item.id, event)}
				>
					{item.label}
				</a>
			{/each}
		</div>

		<div class="mx-auto max-w-3xl text-center md:mx-0 md:text-left md:pl-2 my-16 sm:mt-8">
			<h1 class="font-heading text-xl min-[425px]:text-2xl sm:text-3xl font-bold leading-tight md:text-4xl">
				Web3: The B4A Synergy
			</h1>
			<p class="mt-3 text-sm min-[425px]:text-lg text-white/90 md:text-xl">
				Your blueprint for success in Web3 frontier.
			</p>
		</div>
	</div>
</header>

<main id="main-content" class="w-full flex-1 flex flex-col">
	<section
		id="about"
		class="mx-auto max-w-6xl items-center gap-10 px-5 py-14 md:grid md:grid-cols-[1fr_auto] md:px-8 md:py-20"
	>
		<div class="space-y-4 md:order-2">
			<h2 class="font-heading text-2xl font-semibold text-gray-900">About Us</h2>
			<p class="text-sm leading-relaxed text-gray-800 md:text-base">Your partner for navigating the crypto frontier</p>
			<p class="text-sm leading-relaxed text-gray-700 md:text-base">
				At B4A, we are dedicated to navigating the complex crypto frontier with unparalleled precision. We understand the evolving
				demands of Web2 and the transformative potential of Web3.
			</p>
			<p class="text-sm leading-relaxed text-gray-700 md:text-base">
				Our core expertise lies in meticulously integrating every phase of your project—from the foundational insights of crypto
				ideation and visionary design to robust development, impactful marketing, and strategic consultancy.
			</p>
			<a href="#contact" class="inline-flex items-center justify-center bg-primary px-4 py-2 text-sm font-semibold text-white shadow transition hover:bg-sky-500"
				>Read More</a
			>
		</div>
		<div class="mx-auto w-56 overflow-hidden rounded shadow-lg md:mx-0 md:w-64 mt-16 md:order-1">
			<img
				src={about}
				alt="Illustration of Web3 development"
				width="256"
				height="256"
				class="h-full w-full object-cover"
				loading="lazy"
			/>
		</div>
	</section>

	<section id="testimonials" class="bg-primary py-12 text-white md:py-16">
		<div class="mx-auto flex max-w-6xl flex-col gap-8 px-5 md:px-8">
			<div class="text-center">
				<h2 class="font-heading text-2xl font-semibold">Testimonials</h2>
				<p class="mt-2 text-base text-white/90">Their Success. Our Synergy.</p>
			</div>
			<div class="grid gap-4 md:grid-cols-3">
				{#each testimonials as quote}
					<article class="rounded bg-white/10 p-4 text-sm leading-relaxed shadow">
						<p>{quote}</p>
					</article>
				{/each}
			</div>
		</div>
	</section>

	<section id="contact" class="bg-accent text-white mt-auto">
		<div class="mx-auto grid max-w-6xl gap-10 px-5 py-14 md:grid-cols-2 md:px-8">
			<div aria-labelledby="contact-heading" class="space-y-6">
				<div>
					<p class="text-sm uppercase tracking-wide text-gray-300">Contact Us</p>
					<h3 id="contact-heading" class="font-heading text-xl font-semibold text-white">Send us a message</h3>
				</div>
				<form class="space-y-4" id="contact-form" action="#" method="post" on:submit={handleSubmit}>
					<div class="space-y-2">
						<label for="full-name" class="text-sm text-gray-200">Full Name</label>
						<input
							id="full-name"
							name="name"
							type="text"
							required
							class="w-full rounded border border-gray-500 bg-white/90 px-3 py-2 text-gray-900 outline-none ring-primary focus:ring"
							placeholder="Full Name"
							autocomplete="off"
						/>
					</div>
					<div class="space-y-2">
						<label for="message" class="text-sm text-gray-200">Your Message</label>
						<textarea
							id="message"
							name="message"
							rows="4"
							required
							class="w-full rounded border border-gray-500 bg-white/90 px-3 py-2 text-gray-900 outline-none ring-primary focus:ring"
							placeholder="Your Message"
						></textarea>
					</div>
					<button
						type="submit"
						class="inline-flex items-center justify-center rounded bg-white px-6 py-2 text-sm font-semibold text-gray-900 shadow transition hover:bg-gray-100"
					>
						Submit
					</button>
				</form>
			</div>

			<div class="grid gap-10 md:grid-cols-2 md:gap-6">
				<div aria-labelledby="sitemap-heading" class="space-y-4">
					<p class="text-sm uppercase tracking-wide text-gray-300">Sitemap</p>
					<h3 id="sitemap-heading" class="font-heading text-xl font-semibold text-white">All of our pages</h3>
					<ul class="space-y-2 text-sm text-gray-200">
						{#each navItems as item}
							<li>
								<a class="hover:text-primary" href={`#${item.id}`} on:click={(event) => handleNav(item.id, event)}>{item.label}</a>
							</li>
						{/each}
					</ul>
				</div>
				<div class="space-y-4 text-sm text-gray-200">
					<img src={logo} alt="B4A logo" width="140" height="112" class="h-16 w-auto -ml-1" loading="lazy" />
					<div class="flex items-center gap-2 mt-2">
						<svg class="h-5 w-5 text-primary" viewBox="0 0 24 24" aria-hidden="true" fill="currentColor">
							<path
								d="M6.62 10.79a15.05 15.05 0 006.59 6.59l2.2-2.2a1 1 0 011.01-.24 11.36 11.36 0 003.56.57 1 1 0 011 1v3.61a1 1 0 01-.91 1A17 17 0 013 5.91 1 1 0 014 5h3.61a1 1 0 011 1 11.36 11.36 0 00.57 3.56 1 1 0 01-.24 1.01z"
							/>
						</svg>
						<a href={`tel:${phoneNumber}`} class="hover:text-primary">{phoneNumber}</a>
					</div>
					<div class="flex items-center gap-3 mt-6">
						<a href="https://x.com" target="_blank" aria-label="Visit us on X" class="inline-flex h-8 w-8 items-center justify-center">
							<svg width="62" height="60" viewBox="0 0 62 60" fill="none" xmlns="http://www.w3.org/2000/svg">
								<mask id="mask0_39_141" style="mask-type: luminance" maskUnits="userSpaceOnUse" x="0" y="0" width="62" height="60">
									<path d="M0.281738 0H61.0999V60H0.281738V0Z" fill="white" />
								</mask>
								<g mask="url(#mask0_39_141)">
									<path
										d="M48.1761 2.81152H57.503L37.1289 25.843L61.0999 57.1887H42.3332L27.6239 38.1815L10.812 57.1887H1.47638L23.2667 32.5458L0.281738 2.81581H19.5263L32.8021 20.1858L48.1761 2.81152ZM44.8962 51.6687H50.0658L16.7026 8.04438H11.1595L44.8962 51.6687Z"
										fill="white"
									/>
								</g>
							</svg>
						</a>
						<a href="https://t.me" target="_blank" aria-label="Join us on Telegram" class="inline-flex h-8 w-8 items-center justify-center">
							<svg width="76" height="76" viewBox="0 0 76 76" fill="none" xmlns="http://www.w3.org/2000/svg">
								<path
									d="M66.5002 15.8333L6.3335 39.5833L28.5002 42.7499M66.5002 15.8333L58.5835 63.3333L28.5002 42.7499M66.5002 15.8333L28.5002 42.7499M28.5002 42.7499V60.1666L38.7887 49.7894"
									stroke="white"
									stroke-width="3.75"
									stroke-linecap="round"
									stroke-linejoin="round"
								/>
							</svg>
						</a>
					</div>
				</div>
			</div>
		</div>
	</section>
</main>

<footer class="bg-gray-800 py-3 text-center text-xs text-gray-300 w-full">
	&copy; 2025 All Right Reserved Blockchain4Africa Limited
</footer>
