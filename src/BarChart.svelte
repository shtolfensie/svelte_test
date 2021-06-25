<script>
	import { onMount, afterUpdate } from 'svelte';
	import Chart from 'chart.js/auto'; // imports everything - just for testing and dev
	import Bar from 'svelte-chartjs/src/Bar.svelte';

	export let data;
	export let id;
	export let handleMove;

	//data.options.maintainAspectRatio = false;

	$: ({title, labels, datasets, options} = data);
	$: chartData = {labels, datasets};

	console.log(data);


	/* let canvas;// = document.querySelector('#chart-canvas'); */
	/* let chart; */
	/* let createChart = () => { */
	/* 	chart = new Chart(canvas, { */
	/* 		type: 'bar', */
	/* 		data: { */
	/* 			labels: labels, */
	/* 			datasets: datasets */
	/* 		}, */
	/* 		options: options */
	/* 	}); */
	/* }; */

	/* afterUpdate(() => { */
	/* 	if (chart) { */
	/* 		chart.destroy(); */
	/* 	} */
	/* 	createChart(); */
	/* }); */

/* options = { */
/*     responsive: true, */
/*     scales: { */
/*       xAxes: [ */
/*         { */
/*           barPercentage: 1, */
/*           gridLines: { */
/*             display: true, */
/*             color: "rgba(0, 0, 0, 0.1)" */
/*           } */
/*         } */
/*       ], */
/*       yAxes: [ */
/*         { */
/*           gridLines: { */
/*             display: true, */
/*             color: "rgba(0, 0, 0, 0.1)" */
/*           }, */
/*           ticks: { */
/*             beginAtZero: true */
/*           } */
/*         } */
/*       ] */
/*     } */
/*   } */
/* chartData = { */
/*     labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"], */
/*     datasets: [ */
/*       { */
/*         label: "% of Votes", */
/*         data: [12, 19, 3, 5, 2, 3], */
/*         backgroundColor: [ */
/*           "rgba(255, 134,159,0.4)", */
/*           "rgba(98,  182, 239,0.4)", */
/*           "rgba(255, 218, 128,0.4)", */
/*           "rgba(113, 205, 205,0.4)", */
/*           "rgba(170, 128, 252,0.4)", */
/*           "rgba(255, 177, 101,0.4)" */
/*         ], */
/*         borderWidth: 2, */
/*         borderColor: [ */
/*           "rgba(255, 134, 159, 1)", */
/*           "rgba(98,  182, 239, 1)", */
/*           "rgba(255, 218, 128, 1)", */
/*           "rgba(113, 205, 205, 1)", */
/*           "rgba(170, 128, 252, 1)", */
/*           "rgba(255, 177, 101, 1)" */
/*         ] */
/*       } */
/*     ] */
/*   }; */

	let handleLeft = () => handleMove('left', id);
	let handleRight = () => handleMove('right', id);

</script>

<div class="card">
<div class="card-header">
	<span on:click={handleLeft}>⇐</span>
	<span on:click={handleRight}>⇒</span>
	{id}:{title}
</div>
	<!-- <canvas id="chart-canvas{id}" class="canvas" bind:this={canvas}></canvas> -->
	<Bar 
		data={chartData}
		{options}
		width={400}
		height={300}
	/>
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
