<script>
	import BarChart from './BarChart.svelte';
	import charts from '../public/chartData.json'

	console.log(charts.charts)
	let chartArray = charts.charts;

	function handleMove (dir, id){
		if (dir === 'left') {
			if (id === 0) return;

			let ch = chartArray.splice(id, 1)[0];
			chartArray.splice(id-1, 0, ch);
			chartArray = chartArray;
			/* chartArray = [ch, ...chartArray]; */
			console.log(chartArray);
		}
		else if (dir === 'right') {
			if (id === chartArray.length - 1) return;

			let ch = chartArray.splice(id, 1)[0];
			chartArray.splice(id+1, 0, ch);
			chartArray = chartArray;
			/* chartArray = [...chartArray, ch]; */
			console.log(chartArray);
		}


	}


</script>

<main>
	<div class="container">
		{#each chartArray as chart, i }
			<BarChart
				id={i}
				data={chart}
				{handleMove}
			/>
		{/each}
	</div>
</main>

<style>
	.container {
		display: flex;
		width: 90vw;
		height: 100vh;
		padding: 10px;
	}
	
</style>
