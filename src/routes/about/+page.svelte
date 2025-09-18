<script>
	import { gsap } from 'gsap';
	import { SplitText } from 'gsap/SplitText';
	import { onMount } from 'svelte';

	onMount(() => {
		let splitHeading = SplitText.create('#text', {
			type: 'chars, words, lines'
		});
		gsap.from(splitHeading.chars, {
			y: 100,
			autoAlpha: 0,
			// delay: 0.1,
			duration: 0.3,
			stagger: 0.05
		});
	});
	export const prerender = true;
</script>

<div class="flex h-screen flex-col">
	<div class="text-[5vh] md:text-[10vh] w-2/3 font-anton leading-tight tracking-wide" id="text">
		ABOUT ME
	</div>
	<div class="py-10">
		<div
			class="p-10 w-2/3 bg-white h-fit rounded-lg border-[0.1px] shadow-md hover:shadow-lg transition-all duration-230"
		>
			<ul class="list flex flex-col gap-1 pl-5 space-y-2 text-gray-700">
				<li>I'm a coffee sipping programmer who loves crafting digital solutions.</li>
				<li>
					I'm skilled in a wide range of technologies, from web development to embedded systems.
				</li>
				<li>
					On the web development front, I'm proficient in both front-end and back-end development.
				</li>
				<li>
					I use languages like
					<b class="font-bold">JavaScript</b>, <b class="font-bold">HTML</b>, and
					<b class="font-bold">CSS</b> to create dynamic and visually appealing user interfaces.
				</li>
				<li>
					I've worked with popular frameworks like
					<b class="font-bold">React</b>, <b class="font-bold">Vue</b>, and
					<b class="font-bold">Angular</b> to build complex web applications.
				</li>
				<li>
					On the back-end, I've gained experience with <b class="font-bold">Python</b>,
					<b class="font-bold">Node.js</b>, and frameworks like
					<b class="font-bold">Django</b> and <b class="font-bold">Express</b> to power server-side logic
					and data management.
				</li>
				<li>
					I also work with full-blown enteprise applications and build apps with
					<b class="font-bold">Frappe</b>.
				</li>
			</ul>
		</div>
	</div>
	<div>
		<p class="text-3xl font-thin">Experience</p>
	</div>
</div>
