<script setup>
import { ref, onMounted, createApp } from "vue";

class Link {
	// title: String;
	// gradientColors: Array<String>;
	// para: String;
	// link: String;
	constructor(title, gradientColors, para, link) {
		this.title = title;
		this.gradientColors = gradientColors;
		this.para = para;
		this.link = link;
	}
}

const skills = ref([
	new Link(
		"Vue JS",
		["rgb(67,211,147)", "rgb(96,136,245)"],
		"My right hand ❤, with over 5 projects, 10 small projects, and with 1 year of experience.",
		"https://vuejs.org/"
	),
	new Link(
		"Nuxt JS",
		["rgb(129,239,192)", "rgb(0,220,130)"],
		"My go-to framework ❤, with over 5 projects, 10 small projects, and with 8 months of experience.",
		"https://nuxt.com/"
	),
	new Link(
		"Javascript",
		["rgb(252,221,1)", "rgb(252,221,1)"],
		"My go-to framework ❤, with over 5 projects, 10 small projects, and with 2 year of experience.",
		"https://developer.mozilla.org/en-US/docs/Web/javascript"
	),
	new Link(
		"Vuetify JS",
		["rgb(174,220,254)", "rgb(22,150,247)"],
		"With over 5 projects, 10 small projects, and with 1 year of experience.",
		"https://vuetifyjs.com/"
	),
	new Link(
		"Tailwind CSS",
		["rgb(56,189,248)", "rgb(106,130,246)"],
		"With over 5 projects, 10 small projects, and with 1 year of experience.",
		"https://tailwindcss.com/"
	),
	new Link(
		"SCSS",
		["rgb(207,100,154)", "rgb(207,100,154)"],
		"With over 5 projects, 10 small projects, and with 1 year of experience.",
		"https://sass-lang.com/"
	),
	new Link(
		"Git",
		["rgb(244,76,39)", "rgb(244,76,39)"],
		"With over 5 projects, 10 small projects, and with 1 year of experience.",
		"https://git-scm.com/"
	),
	new Link(
		"BitBucket",
		["rgb(38,133,254)", "rgb(38,133,254)"],
		"My work place ❤, with over 5 projects, 10 small projects, and with 1 year of experience.",
		"https://bitbucket.org/"
	),
	new Link(
		"Github",
		["rgb(255,254,254)", "rgb(255,254,254)"],
		"My work place ❤, with over 5 projects, 10 small projects, and with 1 year of experience.",
		"https://github.com/"
	),
]);
const cardsDiv = ref()

onMounted(() => {
	cardsDiv.value.onmousemove = (e) => {
		for (const card of document.getElementsByClassName("card")) {
			const rect = card.getBoundingClientRect(),
				x = e.clientX - rect.left,
				y = e.clientY - rect.top;

			card.style.setProperty("--mouse-x", `${x}px`);
			card.style.setProperty("--mouse-y", `${y}px`);
		}
	};
});
</script>

<template>
	<div class="flex flex-col h-full items-center">
		<h1 class="text-5xl font-bold text-gradient loop">My skills.</h1>
		<div>
			<div class="md:text-xl text-lg text-white">
				List of my skills gathered throughout a year.
			</div>
		</div>

		<div
			ref="cardsDiv"
			class="w-full cards text-left inline-grid gap-4 md:grid-cols-3 sm:grid-cols-2 grid-cols-1 grid-flow-row-dense mt-10"
		>
			<div
				class="card w-full flex items-center justify-start glass-morphism min-h-[150px] p-2"
				v-for="(each, index) in skills"
				:key="index"
			>
				<div class="w-3/12 h-full grid place-items-center text-center">
					<a
						:href="each.link"
						target="_blank"
						class="text-white text-xl"
						:style="`background: linear-gradient(90deg, ${each.gradientColors[0]}, ${each.gradientColors[1]});`"
						style="
							word-spacing: 999px;
							-webkit-background-clip: text;
							background-clip: text;
							-webkit-text-fill-color: transparent;
						"
					>
						{{ each.title }}
					</a>
				</div>
				<div class="m-2 w-9/12">
					<p class="text-gray-300 leading-5">{{ each.para }}</p>
				</div>
			</div>
		</div>
	</div>
</template>

<style src="@/assets/css/skills.css" scoped></style>
