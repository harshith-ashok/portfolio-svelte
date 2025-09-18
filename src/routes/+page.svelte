<script>
	import { gsap } from 'gsap';
	import { ScrambleTextPlugin } from 'gsap/ScrambleTextPlugin';
	import { SplitText } from 'gsap/SplitText';
	import { onMount } from 'svelte';
	const skills = ['Python', 'Angular', 'Frappe', 'Typescript', 'NodeJS', 'SvelteKit'];
	const projects = [
		{
			name: 'Diabetes Risk Prediction',
			description:
				'Project to learn different concepts in prediction and is a simple tool to visualize different features which is used to predict if the patient has diabetes.',
			link: 'https://github.com/harshith-ashok/diabetes-prediction-ml',
			live: '',
			langs: ['python', 'jupyter', 'pandas']
		},
		{
			name: 'Insurance Claim AI Agent',
			description:
				'This system allows users to upload insurance documents (PDF, Word, HTML) and ask natural-language questions',
			link: 'https://github.com/harshith-ashok/llm_insurance_claim_assistant_api',
			live: '',
			langs: ['python', 'fastapi', 'ollama']
		},
		{
			name: 'Weather App',
			description: 'Stay informed with accurate weather data powered by OpenWeatherMap.',
			link: 'https://github.com/harshith-ashok/atmos',
			live: 'https://atmos-ashen.vercel.app/',
			langs: ['svelte', 'typescript', 'vercel']
		}
	];
	gsap.registerPlugin(ScrambleTextPlugin);
	onMount(() => {
		// gsap.to('#text', 2, {
		// 	scrambleText: {
		// 		text: 'ERP ARCHITECT AND FULL STACK DEVELOPER.',
		// 		chars: 'uppercase'
		// 	}
		// });
		let splitHeading = SplitText.create('#text', {
			type: 'chars, words, lines'
		});
		let split = SplitText.create('#skill', {
			type: 'chars, words, lines'
		});
		gsap.from(split.lines, {
			y: 100,
			autoAlpha: 0,
			delay: 0.5,
			stagger: 0.05
		});
		gsap.from(splitHeading.words, {
			y: 100,
			autoAlpha: 0,
			// delay: 0.1,
			duration: 0.5,
			stagger: 0.05
		});
	});
</script>

<main>
	<div class="text-[5vh] md:text-[10vh] w-2/3 font-anton leading-tight tracking-wide" id="text">
		OPEN ERP AND FULL STACK DEVELOPER.
	</div>
	<div class="w-[50%] py-4 text-xl">
		Hello, I am Harshith Ashok a backend main jack-of-all trades trying to master something. I am
		working on AI/ML and Low-Level Languages for hitting the all important LeetCode Stats
	</div>
	<div>
		<div class="flex gap-2 pt-5">
			<button
				class="inline-block cursor-pointer items-center justify-center rounded-xl border-[1.58px] border-zinc-600 bg-zinc-950 px-5 py-3 font-medium text-slate-200 shadow-md transition-all duration-300 hover:[transform:translateY(-.335rem)] hover:shadow-xl"
			>
				<a href="https://github.com/harshith-ashok" target="_blank">GitHub</a>
			</button>
			<button
				class="inline-block cursor-pointer items-center justify-center rounded-xl border-[1.58px] border-zinc-600 bg-blue-900 px-5 py-3 font-medium text-slate-200 shadow-md transition-all duration-300 hover:[transform:translateY(-.335rem)] hover:shadow-xl"
			>
				<a href="https://linkedin.com/in/harshith-ashok" target="_blank">LinkedIn</a>
			</button><button
				class="inline-block cursor-pointer items-center justify-center rounded-xl border-[1.58px] border-zinc-600 bg-red-900 px-5 py-3 font-medium text-slate-200 shadow-md transition-all duration-300 hover:[transform:translateY(-.335rem)] hover:shadow-xl"
			>
				<a href="https://reddit.com/u/harshith-ashok" target="_blank">Reddit</a>
			</button><button
				class="inline-block cursor-pointer items-center justify-center rounded-xl border-[1.58px] border-zinc-600 bg-yellow-900 px-5 py-3 font-medium text-slate-200 shadow-md transition-all duration-300 hover:[transform:translateY(-.335rem)] hover:shadow-xl"
			>
				<a href="mailto:harshith.7k10@gmail.com" target="_blank">Email</a>
			</button>
		</div>
		<span class="flex items-center py-10 w-[40%]">
			<span class="h-px flex-1 bg-gray-300 dark:bg-gray-600"></span>
		</span>
		<p class="text-3xl font-thin">Key Skills</p>
		<div class="flex">
			<div class="flex flex-col gap-5 w-1/2 py-10">
				{#each skills as skill}
					<div
						id="skill"
						class="font-black text-[#041101] text-5xl md:text-8xl uppercase font-anton tracking-wide hover:translate-x-[50px] transition-all duration-400 cursor-pointer"
					>
						{skill}
					</div>
				{/each}
			</div>
			<div class="p-10 rounded-xl border-1 w-full mr-10">
				<div class="flex flex-col">
					<div>
						<p class="text-3xl font-thin">Diabetes Prediction</p>
						<div class="pt-5 w-3/4">
							This project is a simple, educational tool designed to explore and visualize various
							features used in predicting diabetes. It serves as a hands-on introduction to
							fundamental concepts in machine learning and data visualization for predictive
							modeling.
						</div>
						<div class="pt-10">
							<img src="/insulin.png" class="border-1 rounded-md" alt="" srcset="" />
						</div>
					</div>
					<div></div>
				</div>
			</div>
		</div>
		<div>
			<div class="py-25">
				<p class="text-3xl font-thin">Projects</p>
				<div class="pt-5 grid grid-cols-1 lg:grid-cols-3 justify-start w-3/4 gap-10">
					{#each projects as project}
						<div
							class="bg-white h-64 rounded-lg border-[0.1px] shadow-md hover:shadow-lg transition-all duration-230 hover:translate-1"
						>
							<!-- <div class="flex p-2 gap-1">
								<div>
									<span class="bg-red-500 inline-block center w-3 h-3 rounded-full"></span>
								</div>
								<div>
									<span class="bg-yellow-500 inline-block center w-3 h-3 rounded-full"></span>
								</div>
								<div>
									<span class="bg-green-500 box inline-block center w-3 h-3 rounded-full"></span>
								</div>
							</div> -->
							<div class="p-3 flex gap-3 flex-col">
								<div class="font-bold text-lg">{project.name}</div>
								<div>
									{project.description}
								</div>
								<div class="flex gap-2">
									<a
										href={project.link}
										class="text-sm leading-none border-b-1 transition-all uppercase font-gsans tracking-wider duration-230 hover:bg-black p-1 hover:text-white"
										>Link</a
									>
									<a
										href={project.live}
										class:hidden={project.live == ''}
										class="text-sm leading-none border-b-1 transition-all uppercase font-gsans tracking-wider duration-230 hover:bg-black p-1 hover:text-white"
										>Live</a
									>
								</div>
								<div class="flex gap-1">
									{#each project.langs as lang}
										<p
											class="text-sm w-fit uppercase font-gsans tracking-wider bg-black p-1 text-white cursor-pointer hover:text-black hover:bg-white transition-all duration-230"
										>
											{lang}
										</p>
									{/each}
								</div>
							</div>
						</div>
					{/each}
				</div>
			</div>
		</div>
	</div>
</main>
