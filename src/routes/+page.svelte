<script>
	// @ts-nocheck
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';
	import { ScrollTrigger } from 'gsap/ScrollTrigger';

	gsap.registerPlugin(ScrollTrigger);

	let hero;
	let introText;

	const skills = [
		{
			name: 'Python',
			project: {
				name: 'Diabetes Risk Prediction',
				description:
					'Project to learn different concepts in prediction and is a simple tool to visualize different features which is used to predict if the patient has diabetes.',
				image: 'https://images.unsplash.com/photo-1576091160399-112ba8d25d1d?w=800&h=600&fit=crop',
				link: 'https://github.com/harshith-ashok/diabetes-prediction-ml'
			}
		},
		{
			name: 'Angular',
			project: {
				name: 'Enterprise Dashboard',
				description:
					'A comprehensive enterprise-level dashboard built with Angular featuring real-time data visualization and advanced analytics capabilities.',
				image: 'https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=800&h=600&fit=crop',
				link: '#'
			}
		},
		{
			name: 'Frappe',
			project: {
				name: 'ERP System Module',
				description:
					'Custom ERP module developed using Frappe framework to streamline business operations and automate workflows.',
				image: 'https://images.unsplash.com/photo-1454165804606-c3d57bc86b40?w=800&h=600&fit=crop',
				link: '#'
			}
		},
		{
			name: 'Typescript',
			project: {
				name: 'Type-Safe API Client',
				description: 'A fully type-safe REST API client library built with TypeScript.',
				image: 'https://images.unsplash.com/photo-1555949963-ff9fe0c870eb?w=800&h=600&fit=crop',
				link: '#'
			}
		},
		{
			name: 'NodeJS',
			project: {
				name: 'Insurance Claim AI Agent',
				description: 'Users upload insurance documents and query them using FastAPI and Ollama.',
				image: 'https://images.unsplash.com/photo-1563986768609-322da13575f3?w=800&h=600&fit=crop',
				link: 'https://github.com/harshith-ashok/llm_insurance_claim_assistant_api'
			}
		},
		{
			name: 'SvelteKit',
			project: {
				name: 'Weather App',
				description: 'Weather app powered by OpenWeatherMap, built with Svelte.',
				image: 'https://images.unsplash.com/photo-1592210454359-9043f067919b?w=800&h=600&fit=crop',
				link: 'https://github.com/harshith-ashok/atmos'
			}
		}
	];

	const projects = [
		{
			name: 'Diabetes Risk Prediction',
			description: 'Visual ML-based tool to understand diabetes risk factors.',
			link: 'https://github.com/harshith-ashok/diabetes-prediction-ml',
			live: '',
			langs: ['python', 'pandas', 'ml']
		},
		{
			name: 'Insurance Claim AI Agent',
			description: 'Document-grounded AI assistant for insurance claim analysis.',
			link: 'https://github.com/harshith-ashok/llm_insurance_claim_assistant_api',
			live: '',
			langs: ['python', 'fastapi', 'ollama']
		},
		{
			name: 'Weather App',
			description: 'Minimal weather app using OpenWeatherMap.',
			link: 'https://github.com/harshith-ashok/atmos',
			live: 'https://atmos-ashen.vercel.app/',
			langs: ['svelte', 'typescript', 'vercel']
		}
	];

	let selectedProject = skills[0].project;

	function selectSkill(skill) {
		selectedProject = skill.project;
	}

	function createGrid() {
		const grid = document.getElementById('grid');
		if (!grid) return;

		grid.innerHTML = '';

		const cols = 20;
		const rows = 20;

		for (let i = 0; i < cols; i++) {
			const line = document.createElement('div');
			line.className = 'absolute w-[1px] h-full bg-white';
			line.style.left = `${(i / cols) * 100}%`;
			grid.appendChild(line);

			gsap.to(line, {
				scaleY: Math.random() * 0.6 + 0.4,
				duration: Math.random() * 2 + 1,
				repeat: -1,
				yoyo: true,
				ease: 'sine.inOut'
			});
		}

		for (let i = 0; i < rows; i++) {
			const line = document.createElement('div');
			line.className = 'absolute h-[1px] w-full bg-white';
			line.style.top = `${(i / rows) * 100}%`;
			grid.appendChild(line);

			gsap.to(line, {
				scaleX: Math.random() * 0.6 + 0.4,
				duration: Math.random() * 2 + 1,
				repeat: -1,
				yoyo: true,
				ease: 'sine.inOut'
			});
		}
	}

	onMount(() => {
		createGrid();

		// HERO + INTRO
		const words = hero.querySelectorAll('span');
		gsap.fromTo(
			words,
			{ y: 50, opacity: 0 },
			{
				y: 0,
				opacity: 1,
				duration: 0.8,
				stagger: 0.1,
				ease: 'power3.out',
				onComplete: () => {
					gsap.to(introText, { opacity: 1, y: 0, duration: 1, ease: 'power3.out' });

					// Social buttons animation
					const socialButtons = document.getElementById('socialButtons');
					gsap.to(socialButtons, {
						opacity: 1,
						y: 0,
						duration: 0.8,
						stagger: 0.1,
						ease: 'power3.out'
					});
				}
			}
		);

		// SKILLS
		gsap.fromTo(
			'.skill-item',
			{ opacity: 0, x: -100 },
			{
				opacity: 1,
				x: 0,
				stagger: 0.15,
				duration: 1,
				ease: 'power3.out',
				scrollTrigger: {
					trigger: '.skills-container',
					start: 'top 70%',
					toggleActions: 'play none none none'
				}
			}
		);

		// PROJECTS
		gsap.fromTo(
			'.project-card',
			{ opacity: 0, y: 60 },
			{
				opacity: 1,
				y: 0,
				stagger: 0.2,
				duration: 0.8,
				scrollTrigger: {
					trigger: '.projects-grid',
					start: 'top 70%'
				}
			}
		);
	});
</script>

<main class="bg-black text-white overflow-x-hidden relative">
	<!-- Grid Background (hidden on small screens for performance/layout) -->
	<div id="grid" class="hidden sm:block fixed inset-0 opacity-[0.15] pointer-events-none"></div>

	<div class="container max-w-7xl mx-auto px-4 md:px-8 relative z-10">
		<!-- HERO -->
		<section class="min-h-screen flex items-center overflow-hidden">
			<h1 bind:this={hero} class="hero font-anton text-[10vw] leading-[0.9]">
				<span>OPEN</span>
				<span>ERP</span>
				<span>AND</span>
				<span>FULL</span>
				<span>STACK</span>
				<span>DEVELOPER.</span>
			</h1>
		</section>

		<!-- INTRO + SOCIAL BUTTONS -->
		<section>
			<p
				bind:this={introText}
				id="introText"
				class="text-base md:text-lg max-w-2xl leading-relaxed mb-8 opacity-0 translate-y-6"
			>
				Hello, I am Harshith Ashok a backend main jack-of-all trades trying to master something. I
				am working on AI/ML and Low-Level Languages for hitting the all important LeetCode Stats.
			</p>

			<div class="flex gap-4 flex-wrap mb-8 opacity-0 translate-y-6" id="socialButtons">
				<a
					href="https://github.com/harshith-ashok"
					target="_blank"
					class="btn hover-scale inline-block px-6 py-3 md:px-8 md:py-4 rounded-xl border-[1.5px] border-zinc-600 bg-zinc-950 text-white font-medium shadow-md transition-all duration-300 hover:-translate-y-1 hover:shadow-xl relative overflow-hidden group"
				>
					<span class="relative z-10">GitHub</span>
					<div
						class="absolute top-0 -left-full w-full h-full bg-white/10 transition-all duration-300 group-hover:left-full"
					></div>
				</a>
				<a
					href="https://linkedin.com/in/harshith-ashok"
					target="_blank"
					class="btn hover-scale inline-block px-6 py-3 md:px-8 md:py-4 rounded-xl border-[1.5px] border-zinc-600 bg-blue-900 text-white font-medium shadow-md transition-all duration-300 hover:-translate-y-1 hover:shadow-xl relative overflow-hidden group"
				>
					<span class="relative z-10">LinkedIn</span>
					<div
						class="absolute top-0 -left-full w-full h-full bg-white/10 transition-all duration-300 group-hover:left-full"
					></div>
				</a>
				<a
					href="https://reddit.com/u/harshith-ashok"
					target="_blank"
					class="btn hover-scale inline-block px-6 py-3 md:px-8 md:py-4 rounded-xl border-[1.5px] border-zinc-600 bg-red-900 text-white font-medium shadow-md transition-all duration-300 hover:-translate-y-1 hover:shadow-xl relative overflow-hidden group"
				>
					<span class="relative z-10">Reddit</span>
					<div
						class="absolute top-0 -left-full w-full h-full bg-white/10 transition-all duration-300 group-hover:left-full"
					></div>
				</a>
				<a
					href="mailto:harshith.7k10@gmail.com"
					class="btn hover-scale inline-block px-6 py-3 md:px-8 md:py-4 rounded-xl border-[1.5px] border-zinc-600 bg-yellow-900 text-white font-medium shadow-md transition-all duration-300 hover:-translate-y-1 hover:shadow-xl relative overflow-hidden group"
				>
					<span class="relative z-10">Email</span>
					<div
						class="absolute top-0 -left-full w-full h-full bg-white/10 transition-all duration-300 group-hover:left-full"
					></div>
				</a>
			</div>
		</section>

		<!-- SKILLS -->
		<section class="skills-section py-24">
			<h2 class="text-4xl md:text-6xl mb-12">Key Skills</h2>
			<div class="skills-container grid grid-cols-1 lg:grid-cols-5 gap-12">
				<div class="lg:col-span-2 flex flex-col gap-6">
					{#each skills as skill}
						<button
							class="skill-item font-anton cursor-pointer text-4xl md:text-6xl uppercase text-left transition-colors"
							style="color: {selectedProject.name === skill.project.name ? '#fff' : '#3f3f3f'}"
							onclick={() => selectSkill(skill)}
						>
							{skill.name}
						</button>
					{/each}
				</div>

				<div class="lg:col-span-3 border border-zinc-800 bg-black rounded-2xl p-6 md:p-10">
					<h3 class="text-2xl md:text-4xl mb-6">{selectedProject.name}</h3>
					<p class="text-zinc-400 mb-6">{selectedProject.description}</p>
					<a
						href={selectedProject.link}
						target="_blank"
						class="project-link group inline-flex items-center gap-2 relative text-white text-sm uppercase tracking-wider"
					>
						<span>View Project</span>
						<span class="arrow transition-transform duration-300 group-hover:translate-x-1">→</span>
						<span
							class="underline absolute left-0 -bottom-1 h-[1px] w-full bg-white scale-x-0 origin-left transition-transform duration-300 group-hover:scale-x-100"
						></span>
					</a>
					<img
						src={selectedProject.image}
						alt={selectedProject.name}
						class="mt-8 rounded-lg max-h-[200px] md:max-h-[300px] w-full object-cover"
					/>
				</div>
			</div>
		</section>

		<!-- PROJECTS -->
		<section class="projects-section py-24">
			<h2 class="text-4xl md:text-6xl mb-12">Projects</h2>
			<div class="projects-grid grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
				{#each projects as project}
					<div class="project-card border border-zinc-800 rounded-xl p-6 md:p-8 bg-zinc-950">
						<h3 class="text-xl md:text-2xl mb-4">{project.name}</h3>
						<p class="text-zinc-400 mb-6">{project.description}</p>

						<div class="flex gap-6 mb-4">
							<a
								href={project.link}
								target="_blank"
								class="project-mini-link group relative inline-flex items-center gap-1 text-sm uppercase tracking-wider"
							>
								<span>Link</span>
								<span class="arrow transition-transform duration-300 group-hover:translate-x-1"
									>→</span
								>
								<span
									class="underline absolute left-0 -bottom-1 h-[1px] w-full bg-white scale-x-0 origin-left transition-transform duration-300 group-hover:scale-x-100"
								></span>
							</a>
							{#if project.live}
								<a
									href={project.live}
									target="_blank"
									class="project-mini-link group relative inline-flex items-center gap-1 text-sm uppercase tracking-wider"
								>
									<span>Live</span>
									<span class="arrow transition-transform duration-300 group-hover:translate-x-1"
										>→</span
									>
									<span
										class="underline absolute left-0 -bottom-1 h-[1px] w-full bg-white scale-x-0 origin-left transition-transform duration-300 group-hover:scale-x-100"
									></span>
								</a>
							{/if}
						</div>

						<div class="flex gap-2 flex-wrap">
							{#each project.langs as lang}
								<span class="bg-white text-black px-3 py-1 text-xs uppercase">{lang}</span>
							{/each}
						</div>
					</div>
				{/each}
			</div>
		</section>
	</div>
</main>

<style>
	:global(body) {
		background: #000;
		overflow-x: hidden;
	}
	button:focus {
		outline: none;
	}

	.hero span {
		display: inline-block;
		margin-right: 0.25em;
	}

	.btn {
		cursor: pointer;
	}
</style>
