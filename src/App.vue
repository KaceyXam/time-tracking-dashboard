<script setup lang="ts">
import TimeComponentVue from "./components/TimeComponent.vue";

import json from "./data.json";
</script>

<script lang="ts">
export default {
	data() {
		return {
			lastClicked: "weekly",
		};
	},
};
</script>

<template>
	<section class="tracking-grid">
		<div class="report-element">
			<div class="report-head">
				<img
					src="/images/image-jeremy.png"
					alt="Jeremy Robson Profile Picture"
				/>
				<h2>
					<span class="report-for">Report for</span><br />
					Jeremy Robson
				</h2>
			</div>
			<ul class="selection-list">
				<li>
					<button
						:class="{ active: lastClicked === 'daily' }"
						@click="lastClicked = 'daily'"
					>
						Daily
					</button>
				</li>
				<li>
					<button
						:class="{ active: lastClicked === 'weekly' }"
						@click="lastClicked = 'weekly'"
					>
						Weekly
					</button>
				</li>
				<li>
					<button
						:class="{ active: lastClicked === 'monthly' }"
						@click="lastClicked = 'monthly'"
					>
						Monthly
					</button>
				</li>
			</ul>
		</div>
		<div class="time-components" v-for="object in json">
			<div v-if="lastClicked === 'weekly'">
				<TimeComponentVue
					:title="object.title"
					:timeHrs="object.timeframes.weekly.current"
					:lastHrs="object.timeframes.weekly.previous"
				/>
			</div>
			<div v-if="lastClicked === 'daily'">
				<TimeComponentVue
					:title="object.title"
					:timeHrs="object.timeframes.daily.current"
					:lastHrs="object.timeframes.daily.previous"
				/>
			</div>
			<div v-if="lastClicked === 'monthly'">
				<TimeComponentVue
					:title="object.title"
					:timeHrs="object.timeframes.monthly.current"
					:lastHrs="object.timeframes.monthly.previous"
				/>
			</div>
		</div>
	</section>
</template>

<style scoped>
.tracking-grid {
	display: grid;
	grid-template-columns: repeat(4, 1fr);
	max-width: 1024px;
	width: 90%;
	gap: 1em;
}

.report-element {
	grid-column: 1;
	grid-row: 1 / 3;
	background-color: var(--dark-blue);
	border-radius: 1rem;
}

.report-head {
	background-color: var(--blue);
	padding: 1em;
	display: flex;
	gap: 1rem;
	padding-bottom: 3rem;
	flex-direction: column;
	border-radius: 0.9rem;
}

.report-head img {
	width: 4rem;
	border: solid 2px white;
	border-radius: 999vmax;
}

.report-head h2 {
	font-weight: 300;
	font-size: 32px;
}

.report-for {
	font-size: 0.8rem;
}

.selection-list {
	list-style: none;
	display: flex;
	flex-direction: column;
	gap: 0.5em;
	padding: 1em;
}

.selection-list li button {
	border: none;
	background: none;
	color: var(--pale-blue);
	font-size: 16px;
	cursor: pointer;
}

.selection-list li button:hover {
	color: white;
}

.selection-list li button.active {
	color: white;
}

@media (max-width: 900px) {
	.tracking-grid {
		grid-template-columns: 1fr;
		margin-block: 4rem;
	}

	.report-element {
		grid-row: 1;
		grid-column: 1;
	}

	.report-head {
		flex-direction: row;
		padding-bottom: 1.5rem;
	}

	.selection-list {
		flex-direction: row;
		justify-content: space-between;
		max-width: 350px;
		margin-inline: auto;
	}
}
</style>
