<!-- Script -->
<script setup lang="ts">
// Imports
import { ref } from "vue";

// Variables
let computedStyle = getComputedStyle(document.body);

// Main
let mainColorsTransparency = ref(1);
let main = {
	colors: [
		"red",
		"orange",
		"yellow",
		"green",
		"cyan",
		"blue",
		"purple",
		"magenta",
		"white-light",
		"white",
		"white-dark",
		"gray-light",
		"gray",
		"gray-dark",
		"black-light",
		"black",
		"black-dark",
	],
};

// Colors
let colorsColorsOriginal = ref(true);
let colorsColorsTransparency = ref(1);
let colors = {
	colors: [
		"red-light",
		"red",
		"red-dark",
		"red-deep",
		"orange-light",
		"orange",
		"orange-dark",
		"orange-deep",
		"yellow-light",
		"yellow",
		"yellow-dark",
		"yellow-deep",
		"green-light",
		"green",
		"green-dark",
		"green-deep",
		"cyan-light",
		"cyan",
		"cyan-dark",
		"cyan-deep",
		"blue-light",
		"blue",
		"blue-dark",
		"blue-deep",
		"purple-light",
		"purple",
		"purple-dark",
		"purple-deep",
		"magenta-light",
		"magenta",
		"magenta-dark",
		"magenta-deep",
		"peach-light",
		"peach",
		"peach-dark",
		"peach-deep",
		"brown-light",
		"brown",
		"brown-dark",
		"brown-deep",
		"white-light",
		"white",
		"white-dark",
		"gray-light",
		"gray",
		"gray-dark",
		"black-light",
		"black",
		"black-dark",
	],
};
</script>

<!-- Template -->
<template>
	<main>
		<!-- Title -->
		<h1>DmmD.css Demo</h1>

		<!-- Main -->
		<section id="main">
			<h2>dmmd.css</h2>
			<h3>Colors</h3>
			<div class="main-colors">
				<div class="main-color" v-for="color in main.colors">
					<div
						class="main-color-block"
						:style="{
							'background-color': `rgba(var(--dmmd-color-${color}), ${mainColorsTransparency})`,
						}"
					></div>
					<p>{{ color }}</p>
					<p>
						{{
							computedStyle.getPropertyValue(
								"--dmmd-color-" + color
							)
						}}
					</p>
					<p>
						{{
							"#" +
							computedStyle
								.getPropertyValue("--dmmd-color-" + color)
								.split(", ")
								.map((value) =>
									Number(value).toString(16).padStart(2, "0")
								)
								.join("")
								.toUpperCase()
						}}
					</p>
				</div>
			</div>
			<div id="main-colors-configuration">
				<input
					id="main-colors-transparency"
					type="range"
					min="0"
					max="1"
					step="0.01"
					v-model="mainColorsTransparency"
				/>
				<label for="main-colors-transparency"
					>Transparency: {{ mainColorsTransparency }}</label
				>
			</div>
			<div class="download">
				<a href="./dmmd.css" download>Download</a>
				<a href="https://cdn.iipython.dev/dmmd/v1.2/dmmd.css">CDN</a>
				<a href="https://cdn.iipython.dev/dmmd/v1.2/dmmd.min.css">CDN (Min)</a>
			</div>
		</section>

		<!-- Colors -->
		<section id="colors">
			<h2>dmmd-colors.css</h2>
			<h3>Colors</h3>
			<div class="colors-colors">
				<div
					class="colors-color"
					v-for="color in colorsColorsOriginal
						? colors.colors
						: colors.colors.filter(
								(value) => !main.colors.includes(value)
						  )"
				>
					<div
						class="colors-color-block"
						:style="{
							'background-color': `rgba(var(--dmmd-color-${color}), ${colorsColorsTransparency})`,
						}"
					></div>
					<p>{{ color }}</p>
					<p>
						{{
							computedStyle.getPropertyValue(
								"--dmmd-color-" + color
							)
						}}
					</p>
					<p>
						{{
							"#" +
							computedStyle
								.getPropertyValue("--dmmd-color-" + color)
								.split(", ")
								.map((value) =>
									Number(value).toString(16).padStart(2, "0")
								)
								.join("")
								.toUpperCase()
						}}
					</p>
				</div>
			</div>
			<p>* Original colors not included.</p>
			<div id="colors-colors-configuration">
				<input
					id="colors-colors-transparency"
					type="range"
					min="0"
					max="1"
					step="0.01"
					v-model="colorsColorsTransparency"
				/>
				<label for="colors-colors-transparency"
					>Transparency: {{ colorsColorsTransparency }}</label
				>
				<input
					id="colors-colors-original"
					type="checkbox"
					v-model="colorsColorsOriginal"
				/>
				<label for="colors-colors-original">Show Original</label>
			</div>
			<div class="download">
				<a href="./dmmd-colors.css" download>Download</a>
				<a href="https://cdn.iipython.dev/dmmd/v1.0/dmmd-colors.css">CDN</a>
				<a href="https://cdn.iipython.dev/dmmd/v1.0/dmmd-colors.min.css">CDN (Min)</a>
			</div>
		</section>
	</main>
</template>

<!-- App -->
<style scoped>
main {
	display: flex;
	flex-direction: column;
	gap: 50px 0;
}

h1 {
	font-size: 35px;
	line-height: 35px;
	text-align: center;
}

section {
	display: flex;
	flex-direction: column;
	gap: 10px 0;
}

h2 {
	font-size: 20px;
	line-height: 20px;
	text-align: center;
}

.download {
	display: flex;
	gap: 0 10px;
	justify-content: end;
}

.download a {
	color: rgb(var(--dmmd-c-bl));
}
.download a:hover {
	color: rgb(var(--dmmd-c-cy));
}
</style>

<!-- Main -->
<style scoped>
#main .main-colors {
	display: flex;
	flex-wrap: wrap;
	gap: 10px 10px;
}

#main .main-colors .main-color {
	display: flex;
	flex-direction: column;
	gap: 5px 0;
}
#main .main-colors .main-color .main-color-block {
	border-radius: 5px;
	height: 100px;
	width: 100px;
}

#main .main-colors .main-color p {
	text-align: center;
}

#main-colors-configuration {
	align-items: center;
	display: flex;
	gap: 0 10px;
}
</style>

<!-- Colors -->
<style scoped>
#colors .colors-colors {
	display: flex;
	flex-wrap: wrap;
	gap: 10px 10px;
}

#colors .colors-colors .colors-color {
	display: flex;
	flex-direction: column;
	gap: 5px 0;
}
#colors .colors-colors .colors-color .colors-color-block {
	border-radius: 5px;
	height: 100px;
	width: 100px;
}

#colors .colors-colors .colors-color p {
	text-align: center;
}

#colors-colors-configuration {
	align-items: center;
	display: flex;
	gap: 0 10px;
}
</style>
