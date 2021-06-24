<script>
	import { onMount, afterUpdate } from 'svelte';
	import Chart from 'chart.js/auto'; // imports everything - just for testing and dev

	export let labels;
	export let datasets;
	export let options;
	export let title;
	export let id;
	export let handleMove;


	let canvas;// = document.querySelector('#chart-canvas');
	let chart;
	let createChart = () => {
		chart = new Chart(canvas, {
			type: 'bar',
			data: {
				labels: labels,
				datasets: datasets
			},
			options: options
		});
	};

	afterUpdate(() => {
		if (chart) {
			chart.destroy();
		}
		createChart();
	});


	let handleLeft = () => handleMove('left', id);
	let handleRight = () => handleMove('right', id);

</script>

<div class="card">
<div class="card-header">
	<span on:click={handleLeft}>⇐</span>
	<span on:click={handleRight}>⇒</span>
	{id}:{title}
</div>
	<canvas id="chart-canvas{id}" class="canvas" bind:this={canvas}></canvas>
</div>

<style>

	.card {
		width: 400px;
		height: 300px;
		background-color: #eaeaea;
		padding: 0.7rem;
		margin: 0 0.5rem;
		border-radius: 10px;
		display: flex;
		flex-direction: column;
	}

	.card-header {
		flex-grow: 0;

	}

	#chart-canvas {
		width: 100%;
		flex-grow: 2;

	}


</style>
