<script lang="ts">
	import { onMount } from 'svelte';

	let mounted = $state(false);
	let scrollY = $state(0);
	let activeTab = $state<'student' | 'parent' | 'admin' | 'driver'>('student');

	onMount(() => {
		mounted = true;

		const handleScroll = () => {
			scrollY = window.scrollY;
		};

		window.addEventListener('scroll', handleScroll);

		return () => {
			window.removeEventListener('scroll', handleScroll);
		};
	});

	const useCases = {
		student: {
			title: 'For Students',
			subtitle: 'Never Miss Your Ride',
			icon: '🎓',
			color: '#6366f1',
			gradient: 'linear-gradient(135deg, #6366f1, #818cf8)',
			benefits: [
				{ icon: '📍', title: 'Live Bus Tracking', desc: 'See exactly where your bus is in real-time on an interactive map' },
				{ icon: '⏱️', title: 'Accurate ETAs', desc: 'Know precisely when your bus will arrive at your stop' },
				{ icon: '🚨', title: 'Delay Alerts', desc: 'Instant notifications if your bus is running late or route changes' },
				{ icon: '🗺️', title: 'Route Exploration', desc: 'Explore all available routes and find the best stop for you' }
			]
		},
		parent: {
			title: 'For Parents',
			subtitle: 'Complete Peace of Mind',
			icon: '👨‍👩‍👧',
			color: '#8b5cf6',
			gradient: 'linear-gradient(135deg, #8b5cf6, #a78bfa)',
			benefits: [
				{ icon: '🛡️', title: 'Child Safety Tracking', desc: 'Track your child\'s bus journey from pickup to dropoff in real-time' },
				{ icon: '📱', title: 'Board/Exit Alerts', desc: 'Get instant notifications when your child boards or exits the bus' },
				{ icon: '🚦', title: 'Safe Route Monitoring', desc: 'View optimized and verified safe transportation routes' },
				{ icon: '💬', title: 'Direct Communication', desc: 'Contact drivers and administrators directly through the app' }
			]
		},
		admin: {
			title: 'For Administrators',
			subtitle: 'Complete Fleet Control',
			icon: '👔',
			color: '#ec4899',
			gradient: 'linear-gradient(135deg, #ec4899, #f472b6)',
			benefits: [
				{ icon: '📊', title: 'Central Fleet Dashboard', desc: 'Monitor your entire fleet from one powerful central command center' },
				{ icon: '⛽', title: 'Fuel Analytics', desc: 'Track fuel consumption patterns and optimize costs automatically' },
				{ icon: '🎯', title: 'AI Route Optimization', desc: 'Get intelligent route suggestions that save time and money' },
				{ icon: '📈', title: 'Performance Reports', desc: 'Comprehensive analytics on fleet performance and driver metrics' }
			]
		},
		driver: {
			title: 'For Drivers',
			subtitle: 'Drive Smarter, Not Harder',
			icon: '🚗',
			color: '#3b82f6',
			gradient: 'linear-gradient(135deg, #3b82f6, #60a5fa)',
			benefits: [
				{ icon: '🗺️', title: 'Smart Navigation', desc: 'Turn-by-turn directions specifically optimized for bus routes' },
				{ icon: '📝', title: 'Digital Attendance', desc: 'Mark student attendance digitally with a single tap' },
				{ icon: '💡', title: 'Performance Insights', desc: 'Get real-time feedback on driving patterns and efficiency' },
				{ icon: '🔔', title: 'Route Updates', desc: 'Receive instant notifications about route changes or emergencies' }
			]
		}
	};

	const features = [
		{
			title: 'Real-Time GPS Tracking',
			description: 'State-of-the-art GPS technology provides pinpoint accuracy for every vehicle in your fleet.',
			icon: '🛰️',
			image: '/assets/Live Loation.jpg',
			stats: { value: '99.9%', label: 'Accuracy' }
		},
		{
			title: 'Advanced Analytics',
			description: 'Transform raw data into actionable insights with our powerful analytics dashboard.',
			icon: '📊',
			image: '/assets/Dashboard.jpg',
			stats: { value: '40%', label: 'Cost Reduction' }
		},
		{
			title: 'Intelligent Notifications',
			description: 'Smart, contextual alerts keep everyone informed without overwhelming them.',
			icon: '🔔',
			image: '/assets/Notifications.jpg',
			stats: { value: '24/7', label: 'Monitoring' }
		},
		{
			title: 'Dynamic Route Planning',
			description: 'AI-powered algorithms optimize routes for efficiency, safety, and environmental impact.',
			icon: '🗺️',
			image: '/assets/Bus Routes.jpg',
			stats: { value: '30%', label: 'Time Saved' }
		}
	];

	const appScreenshots = [
		{ src: '/assets/LoginPage.jpg', title: 'Secure Login' },
		{ src: '/assets/Dashboard.jpg', title: 'Student Dashboard' },
		{ src: '/assets/Driver_Dashboard.jpg', title: 'Driver Interface' },
		{ src: '/assets/Search Stops.jpg', title: 'Stop Search' }
	];
</script>

<svelte:head>
	<title>YellowShuttl - Smart Fleet Management for Educational Institutions</title>
	<meta name="description" content="Revolutionary fleet management solution for schools and colleges. Real-time tracking, student safety, and environmental consciousness in one platform." />
</svelte:head>

<div class="page">
	<!-- Navigation -->
	<nav class="nav" class:scrolled={scrollY > 50}>
		<div class="nav-content">
			<div class="nav-brand">
				<img src="/assets/yellow-shuttle-logo-512px.jpg" alt="YellowShuttl" class="nav-logo" />
				<span class="nav-name">YellowShuttl</span>
			</div>
			<div class="nav-actions">
				<a href="https://play.google.com/store/apps/details?id=com.yellowshuttl.student" target="_blank" rel="noopener noreferrer" class="nav-link">Download App</a>
				<a href="https://blink42.com" target="_blank" rel="noopener noreferrer" class="nav-cta">Contact Us</a>
			</div>
		</div>
	</nav>

	<!-- HERO SECTION -->
	<section class="hero">
		<div class="hero-grid">
			<div class="hero-content" class:visible={mounted}>
				<div class="hero-badge">
					<span class="badge-dot"></span>
					Powered by Blink42
				</div>

				<h1 class="hero-title">
					The Future of<br />
					<span class="gradient-text">Educational Transport</span>
				</h1>

				<p class="hero-description">
					Transform how your institution manages student transportation with real-time tracking,
					intelligent routing, and uncompromising safety features. Built for schools, loved by everyone.
				</p>

				<div class="hero-stats">
					<div class="stat-card">
						<div class="stat-value">100%</div>
						<div class="stat-label">Visibility</div>
					</div>
					<div class="stat-card">
						<div class="stat-value">50K+</div>
						<div class="stat-label">Daily Rides</div>
					</div>
					<div class="stat-card">
						<div class="stat-value">95%</div>
						<div class="stat-label">Parent Satisfaction</div>
					</div>
				</div>

				<div class="hero-buttons">
					<a href="https://play.google.com/store/apps/details?id=com.yellowshuttl.student" target="_blank" rel="noopener noreferrer" class="btn btn-primary">
						<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
							<path d="M5 12h14M12 5l7 7-7 7"/>
						</svg>
						Download on Play Store
					</a>
					<a href="https://blink42.com" target="_blank" rel="noopener noreferrer" class="btn btn-secondary">
						Learn More
					</a>
				</div>
			</div>

			<div class="hero-visual">
				<div class="phone-mockup">
					<img src="/assets/Dashboard.jpg" alt="YellowShuttl App" class="phone-screen" />
				</div>
				<div class="floating-card card-1">
					<div class="card-icon">🚌</div>
					<div class="card-content">
						<div class="card-title">Live Tracking</div>
						<div class="card-desc">Real-time updates</div>
					</div>
				</div>
				<div class="floating-card card-2">
					<div class="card-icon">⚡</div>
					<div class="card-content">
						<div class="card-title">Instant Alerts</div>
						<div class="card-desc">Stay informed</div>
					</div>
				</div>
				<div class="floating-card card-3">
					<div class="card-icon">🌱</div>
					<div class="card-content">
						<div class="card-title">Eco-Friendly</div>
						<div class="card-desc">30% less emissions</div>
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- USE CASES SECTION -->
	<section class="section use-cases">
		<div class="container">
			<div class="section-header">
				<span class="section-badge">Use Cases</span>
				<h2 class="section-title">Built for Everyone</h2>
				<p class="section-desc">A comprehensive solution designed for every stakeholder in your institution.</p>
			</div>

			<!-- Tab Navigation -->
			<div class="use-case-tabs">
				{#each Object.entries(useCases) as [key, useCase], index}
					<button
						class="use-case-tab"
						class:active={activeTab === key}
						onclick={() => activeTab = key}
						style="--tab-color: {useCase.color}; --delay: {index * 0.1}s"
					>
						<div class="tab-icon">{useCase.icon}</div>
						<div class="tab-info">
							<div class="tab-title">{useCase.title}</div>
							<div class="tab-subtitle">{useCase.subtitle}</div>
						</div>
					</button>
				{/each}
			</div>

			<!-- Tab Content -->
			{#each Object.entries(useCases) as [key, useCase]}
				{#if activeTab === key}
					<div class="use-case-content" style="background: {useCase.gradient}">
						<div class="benefits-grid">
							{#each useCase.benefits as benefit, i}
								<div class="benefit-card" style="--delay: {i * 0.1}s">
									<div class="benefit-icon-large">{benefit.icon}</div>
									<h4>{benefit.title}</h4>
									<p>{benefit.desc}</p>
								</div>
							{/each}
						</div>
					</div>
				{/if}
			{/each}
		</div>
	</section>

	<!-- FEATURES SECTION -->
	<section class="section features">
		<div class="container-wide">
			<div class="section-header">
				<span class="section-badge">Features</span>
				<h2 class="section-title">Powerful Technology, Simple Experience</h2>
				<p class="section-desc">Enterprise-grade capabilities designed for educational institutions.</p>
			</div>

			<div class="features-grid">
				{#each features as feature, i}
					<div class="feature-card" style="--delay: {i * 0.1}s">
						<div class="feature-header">
							<div class="feature-icon-large">{feature.icon}</div>
							<div class="feature-stat">
								<div class="stat-big">{feature.stats.value}</div>
								<div class="stat-small">{feature.stats.label}</div>
							</div>
						</div>
						<div class="feature-image">
							<img src={feature.image} alt={feature.title} />
						</div>
						<div class="feature-content">
							<h3>{feature.title}</h3>
							<p>{feature.description}</p>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</section>

	<!-- APP SHOWCASE -->
	<section class="section app-showcase">
		<div class="container">
			<div class="section-header">
				<span class="section-badge">The App</span>
				<h2 class="section-title">Designed for Delight</h2>
				<p class="section-desc">Beautiful interfaces that make complex fleet management feel effortless.</p>
			</div>

			<div class="app-showcase-grid">
				<div class="showcase-main">
					<div class="phone-frame">
						<div class="phone-notch"></div>
						<img src="/assets/Dashboard.jpg" alt="Main Dashboard" class="showcase-screen" />
					</div>
				</div>
				<div class="showcase-thumbnails">
					{#each appScreenshots as screenshot}
						<div class="thumbnail">
							<img src={screenshot.src} alt={screenshot.title} />
							<span class="thumbnail-title">{screenshot.title}</span>
						</div>
					{/each}
				</div>
			</div>

			<div class="download-section">
				<h3>Get Started Today</h3>
				<p>Download YellowShuttl now and experience the future of educational transport.</p>
				<a href="https://play.google.com/store/apps/details?id=com.yellowshuttl.student" target="_blank" rel="noopener noreferrer" class="download-btn">
					<svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
						<path d="M3,20.5V3.5C3,2.91 3.34,2.39 3.84,2.15L13.69,12L3.84,21.85C3.34,21.6 3,21.09 3,20.5M16.81,15.12L6.05,21.34L14.54,12.85L16.81,15.12M20.16,10.81C20.5,11.08 20.75,11.5 20.75,12C20.75,12.5 20.53,12.9 20.18,13.18L17.89,14.5L15.39,12L17.89,9.5L20.16,10.81M6.05,2.66L16.81,8.88L14.54,11.15L6.05,2.66Z"/>
					</svg>
					Download on Google Play
				</a>
			</div>
		</div>
	</section>

	<!-- IMPACT SECTION -->
	<section class="section impact">
		<div class="container">
			<div class="section-header">
				<span class="section-badge">Impact</span>
				<h2 class="section-title">Creating Positive Change</h2>
				<p class="section-desc">Every journey with YellowShuttl contributes to a better tomorrow.</p>
			</div>

			<div class="impact-grid">
				<div class="impact-card eco">
					<div class="impact-visual">
						<div class="impact-circle"></div>
						<div class="impact-icon">🌍</div>
					</div>
					<h3>Environmental Impact</h3>
					<p>Reduce carbon emissions by up to 30% through intelligent route optimization and encouraging shared transportation over personal vehicles.</p>
					<div class="impact-metrics">
						<div class="metric">
							<strong>2.5M kg</strong>
							<span>CO₂ Saved Annually</span>
						</div>
					</div>
				</div>

				<div class="impact-card safety">
					<div class="impact-visual">
						<div class="impact-circle"></div>
						<div class="impact-icon">🛡️</div>
					</div>
					<h3>Safety First</h3>
					<p>Real-time tracking and driver performance monitoring ensure the highest safety standards, giving parents complete peace of mind.</p>
					<div class="impact-metrics">
						<div class="metric">
							<strong>99.8%</strong>
							<span>Safety Score</span>
						</div>
					</div>
				</div>

				<div class="impact-card efficiency">
					<div class="impact-visual">
						<div class="impact-circle"></div>
						<div class="impact-icon">⚡</div>
					</div>
					<h3>Operational Excellence</h3>
					<p>Data-driven insights help institutions reduce costs, optimize fleet utilization, and improve overall transportation efficiency.</p>
					<div class="impact-metrics">
						<div class="metric">
							<strong>40%</strong>
							<span>Cost Reduction</span>
						</div>
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- FINAL CTA -->
	<section class="section final-cta">
		<div class="container">
			<div class="final-cta-content">
				<div class="cta-text-section">
					<h2>Join Hundreds of Institutions</h2>
					<p>YellowShuttl is already transforming transportation for educational institutions across the country. Be part of the revolution.</p>
					<div class="cta-features">
						<div class="cta-feature">
							<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
								<path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path>
								<polyline points="22 4 12 14.01 9 11.01"></polyline>
							</svg>
							<span>Free 30-day trial</span>
						</div>
						<div class="cta-feature">
							<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
								<path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path>
								<polyline points="22 4 12 14.01 9 11.01"></polyline>
							</svg>
							<span>No credit card required</span>
						</div>
						<div class="cta-feature">
							<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
								<path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path>
								<polyline points="22 4 12 14.01 9 11.01"></polyline>
							</svg>
							<span>Setup assistance included</span>
						</div>
					</div>
					<div class="cta-actions">
						<a href="https://play.google.com/store/apps/details?id=com.yellowshuttl.student" target="_blank" rel="noopener noreferrer" class="btn btn-primary large">
							Get Started Free
						</a>
						<a href="https://blink42.com" target="_blank" rel="noopener noreferrer" class="btn btn-secondary large">
							Schedule Demo
						</a>
					</div>
				</div>
				<div class="cta-visual-section">
					<div class="cta-badge">
						<span>Powered by</span>
						<img src="/assets/blink42_logo.jpg" alt="Blink42" class="blink42-badge-logo" />
					</div>
					<div class="cta-stats-grid">
						<div class="cta-stat-card">
							<div class="cta-stat-value">500+</div>
							<div class="cta-stat-label">Schools</div>
						</div>
						<div class="cta-stat-card">
							<div class="cta-stat-value">50K+</div>
							<div class="cta-stat-label">Students</div>
						</div>
						<div class="cta-stat-card">
							<div class="cta-stat-value">1M+</div>
							<div class="cta-stat-label">Safe Rides</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- FOOTER -->
	<footer class="footer">
		<div class="container">
			<div class="footer-grid">
				<div class="footer-brand">
					<img src="/assets/yellow-shuttle-logo-512px.jpg" alt="YellowShuttl" class="footer-logo" />
					<h4>YellowShuttl</h4>
					<p>Revolutionizing educational transport with technology, safety, and sustainability.</p>
				</div>

				<div class="footer-links">
					<div class="footer-col">
						<h5>Product</h5>
						<a href="https://blink42.com">Features</a>
						<a href="https://blink42.com">Pricing</a>
						<a href="https://play.google.com/store/apps/details?id=com.yellowshuttl.student">Download App</a>
					</div>

					<div class="footer-col">
						<h5>Company</h5>
						<a href="https://blink42.com">About Blink42</a>
						<a href="https://blink42.com">Contact Us</a>
						<a href="https://blink42.com">Careers</a>
					</div>

					<div class="footer-col">
						<h5>Support</h5>
						<a href="https://blink42.com">Help Center</a>
						<a href="https://blink42.com">Documentation</a>
						<a href="https://blink42.com">Privacy Policy</a>
					</div>
				</div>
			</div>

			<div class="footer-bottom">
				<p>&copy; 2025 YellowShuttl by <a href="https://blink42.com" target="_blank" rel="noopener noreferrer">Blink42</a>. Building the future of educational technology.</p>
			</div>
		</div>
	</footer>
</div>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap');

	:global(*) {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}

	:global(body) {
		font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
		background: #ffffff;
		color: #1a1a1a;
		overflow-x: hidden;
		line-height: 1.6;
		-webkit-font-smoothing: antialiased;
	}

	.page {
		width: 100%;
		overflow-x: hidden;
	}

	/* NAVIGATION */
	.nav {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		z-index: 1000;
		padding: 1.5rem 0;
		transition: all 0.3s ease;
	}

	.nav.scrolled {
		background: rgba(255, 255, 255, 0.95);
		backdrop-filter: blur(20px);
		box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
	}

	.nav-content {
		max-width: 1400px;
		margin: 0 auto;
		padding: 0 2rem;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	.nav-brand {
		display: flex;
		align-items: center;
		gap: 0.75rem;
	}

	.nav-logo {
		width: 40px;
		height: 40px;
		border-radius: 10px;
	}

	.nav-name {
		font-weight: 800;
		font-size: 1.25rem;
		color: #1a1a1a;
	}

	.nav-actions {
		display: flex;
		align-items: center;
		gap: 1.5rem;
	}

	.nav-link {
		color: #666;
		text-decoration: none;
		font-weight: 600;
		transition: color 0.3s ease;
	}

	.nav-link:hover {
		color: #1a1a1a;
	}

	.nav-cta {
		padding: 0.75rem 1.5rem;
		background: #1a1a1a;
		color: #fff;
		font-weight: 700;
		border-radius: 12px;
		text-decoration: none;
		transition: all 0.3s ease;
	}

	.nav-cta:hover {
		background: #000;
		transform: translateY(-2px);
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
	}

	/* HERO SECTION */
	.hero {
		padding: 10rem 2rem 6rem;
		background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
		position: relative;
		overflow: hidden;
	}

	.hero::before {
		content: '';
		position: absolute;
		top: -50%;
		right: -20%;
		width: 800px;
		height: 800px;
		background: radial-gradient(circle, rgba(99, 102, 241, 0.1) 0%, transparent 70%);
		border-radius: 50%;
	}

	.hero-grid {
		max-width: 1400px;
		margin: 0 auto;
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 6rem;
		align-items: center;
		position: relative;
		z-index: 1;
	}

	.hero-content {
		opacity: 0;
		transform: translateY(30px);
		transition: all 0.8s cubic-bezier(0.16, 1, 0.3, 1);
	}

	.hero-content.visible {
		opacity: 1;
		transform: translateY(0);
	}

	.hero-badge {
		display: inline-flex;
		align-items: center;
		gap: 0.5rem;
		padding: 0.5rem 1rem;
		background: rgba(99, 102, 241, 0.1);
		border: 1px solid rgba(99, 102, 241, 0.2);
		border-radius: 50px;
		color: #6366f1;
		font-weight: 600;
		font-size: 0.875rem;
		margin-bottom: 2rem;
	}

	.badge-dot {
		width: 8px;
		height: 8px;
		background: #6366f1;
		border-radius: 50%;
		animation: pulse 2s ease-in-out infinite;
	}

	@keyframes pulse {
		0%, 100% { opacity: 1; transform: scale(1); }
		50% { opacity: 0.5; transform: scale(1.2); }
	}

	.hero-title {
		font-size: clamp(2.5rem, 6vw, 4.5rem);
		font-weight: 900;
		line-height: 1.1;
		color: #1a1a1a;
		margin-bottom: 1.5rem;
	}

	.gradient-text {
		background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 50%, #ec4899 100%);
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		background-clip: text;
	}

	.hero-description {
		font-size: 1.25rem;
		color: #666;
		line-height: 1.8;
		margin-bottom: 3rem;
		max-width: 540px;
	}

	.hero-stats {
		display: flex;
		gap: 2rem;
		margin-bottom: 3rem;
		flex-wrap: wrap;
	}

	.stat-card {
		flex: 1;
		min-width: 120px;
		padding: 1.5rem;
		background: white;
		border-radius: 16px;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
	}

	.stat-value {
		font-size: 2rem;
		font-weight: 900;
		color: #6366f1;
		line-height: 1;
		margin-bottom: 0.5rem;
	}

	.stat-label {
		font-size: 0.875rem;
		color: #666;
		font-weight: 600;
	}

	.hero-buttons {
		display: flex;
		gap: 1rem;
		flex-wrap: wrap;
	}

	.btn {
		display: inline-flex;
		align-items: center;
		gap: 0.5rem;
		padding: 1rem 2rem;
		border-radius: 12px;
		font-weight: 700;
		font-size: 1rem;
		text-decoration: none;
		transition: all 0.3s ease;
		cursor: pointer;
		border: none;
	}

	.btn-primary {
		background: #1a1a1a;
		color: #fff;
	}

	.btn-primary:hover {
		background: #000;
		transform: translateY(-2px);
		box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
	}

	.btn-secondary {
		background: white;
		color: #1a1a1a;
		border: 2px solid #e5e5e5;
	}

	.btn-secondary:hover {
		border-color: #1a1a1a;
		transform: translateY(-2px);
	}

	.btn.large {
		padding: 1.25rem 2.5rem;
		font-size: 1.125rem;
	}

	/* HERO VISUAL - FIXED Z-INDEX */
	.hero-visual {
		position: relative;
		display: flex;
		align-items: center;
		justify-content: center;
		height: 600px;
	}

	.phone-mockup {
		width: 300px;
		height: 600px;
		background: #1a1a1a;
		border-radius: 40px;
		padding: 12px;
		box-shadow: 0 40px 80px rgba(0, 0, 0, 0.2);
		position: relative;
		z-index: 5;
		animation: float-phone 6s ease-in-out infinite;
	}

	@keyframes float-phone {
		0%, 100% { transform: translateY(0px); }
		50% { transform: translateY(-20px); }
	}

	.phone-screen {
		width: 100%;
		height: 100%;
		border-radius: 32px;
		object-fit: cover;
	}

	.floating-card {
		position: absolute;
		background: white;
		border-radius: 16px;
		padding: 1rem 1.5rem;
		box-shadow: 0 8px 32px rgba(0, 0, 0, 0.12);
		display: flex;
		align-items: center;
		gap: 1rem;
		animation: float 4s ease-in-out infinite;
		z-index: 10;
	}

	.card-1 {
		top: 8%;
		left: -8%;
		animation-delay: 0s;
	}

	.card-2 {
		top: 45%;
		right: -8%;
		animation-delay: 1s;
	}

	.card-3 {
		bottom: 12%;
		left: -10%;
		animation-delay: 2s;
	}

	@keyframes float {
		0%, 100% { transform: translateY(0px); }
		50% { transform: translateY(-15px); }
	}

	.card-icon {
		font-size: 2rem;
	}

	.card-title {
		font-weight: 700;
		color: #1a1a1a;
		font-size: 0.875rem;
	}

	.card-desc {
		font-size: 0.75rem;
		color: #666;
	}

	/* SECTION COMMON */
	.section {
		padding: 6rem 2rem;
	}

	.container {
		max-width: 1200px;
		margin: 0 auto;
	}

	.container-wide {
		max-width: 1400px;
		margin: 0 auto;
	}

	.section-header {
		text-align: center;
		margin-bottom: 4rem;
	}

	.section-badge {
		display: inline-block;
		padding: 0.5rem 1rem;
		background: rgba(99, 102, 241, 0.1);
		border: 1px solid rgba(99, 102, 241, 0.2);
		border-radius: 50px;
		color: #6366f1;
		font-weight: 700;
		font-size: 0.875rem;
		text-transform: uppercase;
		letter-spacing: 1px;
		margin-bottom: 1rem;
	}

	.section-title {
		font-size: clamp(2rem, 5vw, 3rem);
		font-weight: 900;
		color: #1a1a1a;
		margin-bottom: 1rem;
	}

	.section-desc {
		font-size: 1.25rem;
		color: #666;
		max-width: 700px;
		margin: 0 auto;
	}

	/* USE CASES SECTION - TAB DESIGN */
	.use-cases {
		background: linear-gradient(180deg, #ffffff 0%, #f8f9fa 100%);
	}

	/* Tab Navigation */
	.use-case-tabs {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 1rem;
		margin-bottom: 2rem;
	}

	.use-case-tab {
		background: white;
		border: 2px solid #e5e5e5;
		border-radius: 16px;
		padding: 1.5rem;
		cursor: pointer;
		transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 1rem;
		text-align: center;
		position: relative;
		overflow: hidden;
		animation: fade-in 0.6s ease-out both;
		animation-delay: var(--delay);
	}

	@keyframes fade-in {
		from { opacity: 0; transform: translateY(30px); }
		to { opacity: 1; transform: translateY(0); }
	}

	.use-case-tab::before {
		content: '';
		position: absolute;
		inset: 0;
		background: var(--tab-color);
		opacity: 0;
		transition: opacity 0.3s ease;
		z-index: 0;
	}

	.use-case-tab:hover::before {
		opacity: 0.05;
	}

	.use-case-tab.active::before {
		opacity: 0.1;
	}

	.use-case-tab:hover {
		transform: translateY(-4px);
		border-color: var(--tab-color);
		box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
	}

	.use-case-tab.active {
		border-color: var(--tab-color);
		border-width: 3px;
		box-shadow: 0 8px 32px rgba(0, 0, 0, 0.12);
	}

	.tab-icon {
		font-size: 2.5rem;
		position: relative;
		z-index: 1;
	}

	.tab-info {
		position: relative;
		z-index: 1;
	}

	.tab-title {
		font-size: 1rem;
		font-weight: 800;
		color: #1a1a1a;
		margin-bottom: 0.25rem;
	}

	.tab-subtitle {
		font-size: 0.875rem;
		color: #666;
		font-weight: 600;
	}

	.use-case-tab.active .tab-title {
		color: var(--tab-color);
	}

	/* Tab Content */
	.use-case-content {
		border-radius: 32px;
		padding: 4rem 3rem;
		animation: slide-up 0.5s cubic-bezier(0.16, 1, 0.3, 1);
		box-shadow: 0 8px 32px rgba(0, 0, 0, 0.12);
	}

	@keyframes slide-up {
		from {
			opacity: 0;
			transform: translateY(20px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	.benefits-grid {
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		gap: 2rem;
	}

	.benefit-card {
		background: white;
		border-radius: 20px;
		padding: 2rem;
		transition: all 0.3s ease;
		animation: fade-in 0.5s ease-out both;
		animation-delay: var(--delay);
	}

	.benefit-card:hover {
		transform: translateY(-4px);
		box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
	}

	.benefit-icon-large {
		font-size: 2.5rem;
		margin-bottom: 1rem;
	}

	.benefit-card h4 {
		font-size: 1.25rem;
		font-weight: 800;
		color: #1a1a1a;
		margin-bottom: 0.75rem;
	}

	.benefit-card p {
		font-size: 1rem;
		color: #666;
		line-height: 1.7;
	}

	/* FEATURES SECTION */
	.features {
		background: #ffffff;
	}

	.features-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
		gap: 2rem;
	}

	.feature-card {
		background: white;
		border-radius: 24px;
		overflow: hidden;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
		transition: all 0.4s ease;
		animation: fade-in 0.6s ease-out both;
		animation-delay: var(--delay);
	}

	.feature-card:hover {
		transform: translateY(-10px);
		box-shadow: 0 12px 40px rgba(0, 0, 0, 0.15);
	}

	.feature-header {
		padding: 2rem;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	.feature-icon-large {
		font-size: 3rem;
	}

	.feature-stat {
		text-align: right;
	}

	.stat-big {
		font-size: 2rem;
		font-weight: 900;
		color: #6366f1;
		line-height: 1;
	}

	.stat-small {
		font-size: 0.875rem;
		color: #666;
		font-weight: 600;
	}

	.feature-image {
		height: 300px;
		overflow: hidden;
	}

	.feature-image img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		transition: transform 0.4s ease;
	}

	.feature-card:hover .feature-image img {
		transform: scale(1.05);
	}

	.feature-content {
		padding: 2rem;
	}

	.feature-content h3 {
		font-size: 1.5rem;
		font-weight: 800;
		color: #1a1a1a;
		margin-bottom: 0.75rem;
	}

	.feature-content p {
		color: #666;
		line-height: 1.7;
	}

	/* APP SHOWCASE */
	.app-showcase {
		background: linear-gradient(180deg, #f8f9fa 0%, #ffffff 100%);
	}

	.app-showcase-grid {
		display: grid;
		grid-template-columns: 2fr 1fr;
		gap: 3rem;
		margin-bottom: 4rem;
	}

	.showcase-main {
		display: flex;
		align-items: center;
		justify-content: center;
		background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
		border-radius: 32px;
		padding: 4rem;
		position: relative;
		overflow: hidden;
	}

	.showcase-main::before {
		content: '';
		position: absolute;
		inset: 0;
		background: radial-gradient(circle at 30% 50%, rgba(255, 255, 255, 0.1) 0%, transparent 60%);
	}

	.phone-frame {
		width: 320px;
		height: 640px;
		background: #1a1a1a;
		border-radius: 40px;
		padding: 16px;
		box-shadow: 0 40px 100px rgba(0, 0, 0, 0.4);
		position: relative;
		z-index: 10;
	}

	.phone-notch {
		position: absolute;
		top: 16px;
		left: 50%;
		transform: translateX(-50%);
		width: 120px;
		height: 30px;
		background: #1a1a1a;
		border-radius: 0 0 20px 20px;
		z-index: 20;
	}

	.showcase-screen {
		width: 100%;
		height: 100%;
		border-radius: 32px;
		object-fit: cover;
	}

	.showcase-thumbnails {
		display: flex;
		flex-direction: column;
		gap: 1.5rem;
	}

	.thumbnail {
		position: relative;
		border-radius: 16px;
		overflow: hidden;
		cursor: pointer;
		transition: all 0.3s ease;
	}

	.thumbnail:hover {
		transform: scale(1.05);
		box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15);
	}

	.thumbnail img {
		width: 100%;
		height: 140px;
		object-fit: cover;
		display: block;
	}

	.thumbnail-title {
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		padding: 0.75rem 1rem;
		background: linear-gradient(to top, rgba(0, 0, 0, 0.8), transparent);
		color: white;
		font-weight: 700;
		font-size: 0.875rem;
	}

	.download-section {
		text-align: center;
		background: white;
		border-radius: 24px;
		padding: 3rem;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
	}

	.download-section h3 {
		font-size: 2rem;
		font-weight: 900;
		color: #1a1a1a;
		margin-bottom: 1rem;
	}

	.download-section p {
		font-size: 1.125rem;
		color: #666;
		margin-bottom: 2rem;
	}

	.download-btn {
		display: inline-flex;
		align-items: center;
		gap: 0.75rem;
		padding: 1.25rem 2.5rem;
		background: #1a1a1a;
		color: white;
		font-weight: 700;
		font-size: 1.125rem;
		border-radius: 12px;
		text-decoration: none;
		transition: all 0.3s ease;
	}

	.download-btn:hover {
		background: #000;
		transform: translateY(-2px);
		box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
	}

	/* IMPACT SECTION */
	.impact {
		background: linear-gradient(180deg, #ffffff 0%, #f8f9fa 100%);
	}

	.impact-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
		gap: 2rem;
	}

	.impact-card {
		background: white;
		border-radius: 24px;
		padding: 3rem;
		text-align: center;
		transition: all 0.4s ease;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
	}

	.impact-card:hover {
		transform: translateY(-10px);
		box-shadow: 0 12px 40px rgba(0, 0, 0, 0.12);
	}

	.impact-visual {
		position: relative;
		width: 120px;
		height: 120px;
		margin: 0 auto 2rem;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.impact-circle {
		position: absolute;
		inset: 0;
		border-radius: 50%;
		animation: spin 20s linear infinite;
	}

	.impact-card.eco .impact-circle {
		background: linear-gradient(135deg, rgba(34, 197, 94, 0.2), rgba(74, 222, 128, 0.2));
		box-shadow: 0 0 40px rgba(34, 197, 94, 0.3);
	}

	.impact-card.safety .impact-circle {
		background: linear-gradient(135deg, rgba(99, 102, 241, 0.2), rgba(139, 92, 246, 0.2));
		box-shadow: 0 0 40px rgba(99, 102, 241, 0.3);
	}

	.impact-card.efficiency .impact-circle {
		background: linear-gradient(135deg, rgba(251, 146, 60, 0.2), rgba(251, 191, 36, 0.2));
		box-shadow: 0 0 40px rgba(251, 146, 60, 0.3);
	}

	@keyframes spin {
		from { transform: rotate(0deg); }
		to { transform: rotate(360deg); }
	}

	.impact-icon {
		font-size: 3.5rem;
		position: relative;
		z-index: 10;
	}

	.impact-card h3 {
		font-size: 1.75rem;
		font-weight: 900;
		color: #1a1a1a;
		margin-bottom: 1rem;
	}

	.impact-card p {
		color: #666;
		line-height: 1.8;
		margin-bottom: 2rem;
	}

	.impact-metrics {
		padding-top: 2rem;
		border-top: 2px solid #f8f9fa;
	}

	.metric strong {
		display: block;
		font-size: 2rem;
		font-weight: 900;
		color: #6366f1;
		margin-bottom: 0.5rem;
	}

	.metric span {
		color: #666;
		font-size: 0.875rem;
		font-weight: 600;
	}

	/* FINAL CTA - REDESIGNED */
	.final-cta {
		background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
	}

	.final-cta-content {
		display: grid;
		grid-template-columns: 1.2fr 1fr;
		gap: 4rem;
		align-items: center;
		background: white;
		border-radius: 32px;
		padding: 4rem;
		box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
	}

	.cta-text-section h2 {
		font-size: clamp(2rem, 4vw, 3rem);
		font-weight: 900;
		color: #1a1a1a;
		margin-bottom: 1rem;
	}

	.cta-text-section p {
		font-size: 1.125rem;
		color: #666;
		line-height: 1.8;
		margin-bottom: 2rem;
	}

	.cta-features {
		display: flex;
		flex-direction: column;
		gap: 1rem;
		margin-bottom: 2.5rem;
	}

	.cta-feature {
		display: flex;
		align-items: center;
		gap: 0.75rem;
		color: #1a1a1a;
		font-weight: 600;
	}

	.cta-feature svg {
		color: #4CAF50;
		flex-shrink: 0;
	}

	.cta-actions {
		display: flex;
		gap: 1rem;
		flex-wrap: wrap;
	}

	.cta-visual-section {
		display: flex;
		flex-direction: column;
		gap: 2rem;
	}

	.cta-badge {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 1rem;
		padding: 1.5rem;
		background: linear-gradient(135deg, #f8f9fa, #e9ecef);
		border-radius: 20px;
	}

	.cta-badge span {
		font-size: 0.875rem;
		font-weight: 600;
		color: #666;
		text-transform: uppercase;
		letter-spacing: 1px;
	}

	.blink42-badge-logo {
		height: 80px;
		width: auto;
	}

	.cta-stats-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 1rem;
	}

	.cta-stat-card {
		background: linear-gradient(135deg, #6366f1, #8b5cf6);
		padding: 1.5rem;
		border-radius: 16px;
		text-align: center;
		color: white;
	}

	.cta-stat-value {
		font-size: 2rem;
		font-weight: 900;
		line-height: 1;
		margin-bottom: 0.5rem;
	}

	.cta-stat-label {
		font-size: 0.875rem;
		opacity: 0.9;
	}

	/* FOOTER */
	.footer {
		background: #1a1a1a;
		color: #fff;
		padding: 4rem 2rem 2rem;
	}

	.footer-grid {
		display: grid;
		grid-template-columns: 2fr 3fr;
		gap: 4rem;
		margin-bottom: 3rem;
	}

	.footer-brand {
		max-width: 350px;
	}

	.footer-logo {
		width: 60px;
		height: 60px;
		border-radius: 12px;
		margin-bottom: 1rem;
	}

	.footer-brand h4 {
		font-size: 1.5rem;
		font-weight: 900;
		margin-bottom: 0.75rem;
	}

	.footer-brand p {
		color: #999;
		line-height: 1.7;
	}

	.footer-links {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 3rem;
	}

	.footer-col h5 {
		font-weight: 800;
		margin-bottom: 1.5rem;
		font-size: 1rem;
	}

	.footer-col a {
		display: block;
		color: #999;
		text-decoration: none;
		margin-bottom: 0.75rem;
		transition: color 0.3s ease;
	}

	.footer-col a:hover {
		color: #fff;
	}

	.footer-bottom {
		padding-top: 2rem;
		border-top: 1px solid rgba(255, 255, 255, 0.1);
		text-align: center;
		color: #999;
	}

	.footer-bottom a {
		color: #fff;
		text-decoration: none;
		font-weight: 700;
	}

	/* RESPONSIVE */
	@media (max-width: 1024px) {
		.hero-grid {
			grid-template-columns: 1fr;
			gap: 3rem;
		}

		.hero-visual {
			height: 500px;
		}

		.use-case-tabs {
			grid-template-columns: repeat(2, 1fr);
		}

		.benefits-grid {
			grid-template-columns: 1fr;
		}

		.app-showcase-grid {
			grid-template-columns: 1fr;
		}

		.showcase-thumbnails {
			flex-direction: row;
			overflow-x: auto;
		}

		.thumbnail {
			min-width: 200px;
		}

		.final-cta-content {
			grid-template-columns: 1fr;
			gap: 3rem;
		}

		.footer-grid {
			grid-template-columns: 1fr;
			gap: 3rem;
		}

		.footer-links {
			grid-template-columns: repeat(3, 1fr);
		}
	}

	@media (max-width: 768px) {
		.hero {
			padding: 8rem 1.5rem 4rem;
		}

		.section {
			padding: 4rem 1.5rem;
		}

		.nav-actions {
			gap: 1rem;
		}

		.nav-link {
			display: none;
		}

		.hero-buttons {
			flex-direction: column;
		}

		.btn {
			width: 100%;
			justify-content: center;
		}

		.use-case-tabs {
			grid-template-columns: 1fr;
		}

		.use-case-content {
			padding: 2.5rem 1.5rem;
		}

		.benefits-grid {
			grid-template-columns: 1fr;
		}

		.features-grid {
			grid-template-columns: 1fr;
		}

		.impact-grid {
			grid-template-columns: 1fr;
		}

		.final-cta-content {
			padding: 2.5rem 1.5rem;
		}

		.cta-actions {
			flex-direction: column;
		}

		.cta-stats-grid {
			grid-template-columns: 1fr;
		}

		.footer-links {
			grid-template-columns: 1fr;
		}

		.floating-card {
			display: none;
		}
	}
</style>
