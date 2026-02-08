<script>
	import { gsap } from 'gsap';
	import { SplitText } from 'gsap/SplitText';
	import { onMount } from 'svelte';

	onMount(() => {
		// Split heading animation
		const splitHeading = SplitText.create('#text', {
			type: 'chars, words, lines'
		});

		gsap.fromTo(
			splitHeading.chars,
			{ y: 50, autoAlpha: 0 },
			{
				y: 0,
				autoAlpha: 1,
				duration: 0.5,
				stagger: 0.05,
				ease: 'power3.out'
			}
		);

		// About cards animation
		gsap.fromTo(
			'.about-card',
			{ y: 50, autoAlpha: 0 },
			{
				y: 0,
				autoAlpha: 1,
				duration: 0.8,
				stagger: 0.2,
				delay: 0.3,
				ease: 'power3.out'
			}
		);

		// Create animated grid background
		createGrid();

		// Parallax scroll effect for grid
		gsap.to('#grid', {
			y: 200,
			ease: 'none',
			scrollTrigger: {
				trigger: 'main',
				start: 'top top',
				end: 'bottom top',
				scrub: true
			}
		});
	});

	function createGrid() {
		const grid = document.getElementById('grid');
		if (!grid) return;
		grid.innerHTML = '';

		const cols = 20;
		const rows = 20;

		for (let i = 0; i < cols; i++) {
			const line = document.createElement('div');
			line.className = 'absolute w-[1px] h-full bg-white/10';
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
			line.className = 'absolute h-[1px] w-full bg-white/10';
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
</script>

<main
	class="bg-black text-white min-h-screen flex flex-col items-start px-8 md:px-20 py-16 relative overflow-hidden"
>
	<!-- Animated Grid -->
	<div id="grid" class="fixed inset-0 opacity-20 pointer-events-none z-0"></div>

	<!-- Heading -->
	<div
		id="text"
		class="text-[8vw] md:text-[6rem] font-anton leading-tight tracking-wide mb-12 relative z-10"
	>
		ABOUT ME
	</div>

	<!-- About Card -->
	<div
		class="about-card bg-zinc-900 border border-zinc-700 rounded-2xl p-10 shadow-lg max-w-3xl w-full mb-12 relative z-10 opacity-100"
	>
		<ul class="list-disc pl-6 space-y-3 text-zinc-300 text-lg">
			<li>I'm a coffee sipping programmer who loves crafting digital solutions.</li>
			<li>Skilled in a wide range of technologies, from web development to embedded systems.</li>
			<li>Proficient in both front-end and back-end development for web projects.</li>
			<li>
				I use languages like <b class="text-white font-bold">JavaScript</b>,
				<b class="text-white font-bold">HTML</b>, and <b class="text-white font-bold">CSS</b>.
			</li>
			<li>
				Worked with frameworks like <b class="text-white font-bold">React</b>,
				<b class="text-white font-bold">Vue</b>, and <b class="text-white font-bold">Angular</b>.
			</li>
			<li>
				On the back-end, experienced with <b class="text-white font-bold">Python</b>,
				<b class="text-white font-bold">Node.js</b>, <b class="text-white font-bold">Django</b> and
				<b class="text-white font-bold">Express</b>.
			</li>
			<li>
				I also work with enterprise applications and build apps with <b class="text-white font-bold"
					>Frappe</b
				>.
			</li>
		</ul>
	</div>

	<!-- Experience Section -->
	<div
		class="about-card bg-zinc-900 border border-zinc-700 rounded-2xl p-10 shadow-lg max-w-3xl w-full relative z-10 opacity-100"
	>
		<p class="text-3xl md:text-4xl font-anton mb-6 text-white">Experience</p>
		<ul class="list-disc pl-6 space-y-2 text-zinc-300 text-lg">
			<li>Developed multiple full-stack web applications using modern frameworks.</li>
			<li>Worked on AI/ML projects, implementing prediction and data visualization tools.</li>
			<li>Built ERP modules and automation tools using Frappe framework.</li>
			<li>Created REST APIs and type-safe clients with TypeScript and Node.js.</li>
			<li>Experience with both small-scale projects and large enterprise systems.</li>
		</ul>
	</div>
</main>

<style>
	:global(body) {
		background: #000;
		color: #fff;
		font-family: 'Inter', sans-serif;
	}
	.hero span {
		display: inline-block;
		margin-right: 0.25em;
	}
	.about-card b {
		color: #fff;
	}
	ul li {
		line-height: 1.8;
	}
</style>
