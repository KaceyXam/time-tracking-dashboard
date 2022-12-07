<script lang="ts">
import workIcon from "/icon-work.svg";

export default {
	props: {
		title: String,
		timeHrs: Number,
		lastHrs: Number,
	},
};
</script>

<template>
	<section
		:class="{
			work: title === 'Work',
			play: title === 'Play',
			study: title === 'Study',
			exercise: title === 'Exercise',
			social: title === 'Social',
			selfcare: title === 'Self Care',
		}"
	>
		<div class="time-content">
			<span class="header">
				<h3>{{ title }}</h3>
				<button class="options-btn">
					<svg width="21" height="5" xmlns="http://www.w3.org/2000/svg">
						<path
							d="M2.5 0a2.5 2.5 0 1 1 0 5 2.5 2.5 0 0 1 0-5Zm8 0a2.5 2.5 0 1 1 0 5 2.5 2.5 0 0 1 0-5Zm8 0a2.5 2.5 0 1 1 0 5 2.5 2.5 0 0 1 0-5Z"
							fill-rule="evenodd"
						/>
					</svg>
				</button>
			</span>
			<div class="time">{{ timeHrs }}<span>hrs</span></div>
			<span class="last-week">Last Week - {{ lastHrs }}</span>
		</div>
	</section>
</template>

<style scoped>
section {
	border-radius: 1em;
	width: 100%;
	padding-top: 2rem;
}

section.work {
	background-color: var(--work-red);
}
section.play {
	background-color: var(--play-blue);
}
section.study {
	background-color: var(--study-red);
}
section.exercise {
	background-color: var(--exercise-green);
}
section.social {
	background-color: var(--social-violet);
}
section.selfcare {
	background-color: var(--self-care-orange);
}

.time-content {
	background-color: var(--dark-blue);
	border-radius: 0.9rem;
	display: flex;
	flex-direction: column;
	padding: 1em;
	width: 100%;
	gap: 1em;
	transition: background-color 75ms ease-in-out;
}

.time-content:hover {
	background-color: var(--desat-blue);
	cursor: pointer;
}

.header {
	display: flex;
	justify-content: space-between;
}

.header h3 {
	font-weight: 400;
	font-size: 1rem;
}

.options-btn {
	background: none;
	border: none;
	color: inherit;
	padding: 0;
	cursor: pointer;
}

.options-btn svg {
	fill: var(--pale-blue);
}
.options-btn:hover svg {
	fill: white;
}

.time {
	font-size: 46px;
	font-weight: 300;
}

.time span {
	font-size: 32px;
}

.last-week {
	color: var(--soft-blue);
}

@media (max-width: 900px) {
	.time-content {
		display: grid;
		grid-template-columns: 1fr 1fr;
		align-items: center;
	}

	.header {
		grid-column: 1 / -1;
	}

	.last-week {
		text-align: end;
	}
}
</style>
