<script lang="ts">
	import { page } from '$app/state';
	export const prerender = true;
</script>

<div class="flex flex-col gap-20 items-center">
	<div class="text-[10vh] font-anton leading-tight tracking-wide">
		{page.status}
		{page.error?.message}
	</div>
	<button
		class="bg-white text-center w-48 h-14 relative text-black text-xl font-semibold group cursor-pointer"
		type="button"
		on:click={() => (window.location.href = '/')}
	>
		<div
			class="bg-black h-12 w-1/4 flex items-center justify-center absolute left-1 top-[4px] group-hover:w-[184px] z-10 duration-500"
		>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				fill="none"
				viewBox="0 0 24 24"
				stroke-width="1.5"
				stroke="currentColor"
				class="size-6 text-white"
			>
				<path
					stroke-linecap="round"
					stroke-linejoin="round"
					d="M13.5 4.5 21 12m0 0-7.5 7.5M21 12H3"
				/>
			</svg>
		</div>
		<p class="translate-x-2 pl-2">Home</p>
	</button>
</div>
