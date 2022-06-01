<template>
	<div class="App">
		<h1>Hello TypeScript</h1>
		<header>
			<div class="title">
				Hyrile Jobs
			</div>
			<div class="order">
				<button @click="handleClick('title')">
					Order by title
				</button>
				<button @click="handleClick('location')">
					Order by location
				</button>
				<button @click="handleClick('salary')">
					Order by salary
				</button>
			</div>
		</header>
		<JobList :jobs="jobs" :order="order" />
	</div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from './types/Job';
import JobList from './components/JobList.vue';
import OrderTerm from './types/OrderTerm';

export default defineComponent({
	name: "App",
	setup() {
		const jobs = ref<Job[]>([
			{ title: "MegaHit", location: "Almaty", salary: 250000, id: "1" },
			{ title: "Oscorp", location: "New York", salary: 350000, id: "2" },
			{ title: "Maxima", location: "Aktobe", salary: 1250000, id: "3" },
			{ title: "AsiaPark", location: "Astana", salary: 820000, id: "4" },
			{ title: "Aport", location: "Nur-Sultan", salary: 990000, id: "5" }
		]);

		const order = ref<OrderTerm>('title');

		const handleClick = (term: OrderTerm) => {
			order.value = term;
		}

		return { jobs, handleClick, order };
	},
	components: { JobList }
});
</script>

<style scoped>
header {
	text-align: center;
}

header .order {
	margin-top: 20px;
}

button {
	margin: 0 10px;
	color: blue;
	border: 3px solid blue;
	background: gray;
	padding: 8px 16px;
	border-radius: 4px;
	cursor: pointer;
	font-weight: bold;
}
</style>
