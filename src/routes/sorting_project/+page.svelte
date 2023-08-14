<script>
	let sortingArr = Array.from({ length: 50 }, () => Math.floor(Math.random() * 100));
	let sortingArrUsed = false;

	async function bubbleSort() {
		if (sortingArrUsed) {
			sortingArr = Array.from({ length: 50 }, () => Math.floor(Math.random() * 99) + 1);
		}
		sortingArrUsed = true;

		let moved = true;
		while (moved) {
			moved = false;
			for (let i = 0; i < sortingArr.length - 1; i++) {
				if (sortingArr[i] > sortingArr[i + 1]) {
					let temp = sortingArr[i];
					sortingArr[i] = sortingArr[i + 1];
					sortingArr[i + 1] = temp;
					await new Promise((r) => setTimeout(r, 100));
					moved = true;
				}
			}
		}
	}
</script>

<main>
	<h1>Bubble sorting animation</h1>
	<div id="graph">
		{#each sortingArr as num, i}
			{#if i != sortingArr.length - 1}
				<div class="graph-bar" style="width: 1%; height: {num}%;" />
				<div class="graph-divider" style="width: 0.5%;" />
			{:else}
				<div class="graph-bar" style="width: 1%; height: {num}%" />
			{/if}
		{/each}
	</div>

	<button id="start-bubble-sort" on:click={bubbleSort}> Start the bubble sort! </button>
</main>

<style>
	main {
		padding: 3%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	#graph {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: flex-end;
		height: 60vh;
		width: 80vw;
	}

	.graph-bar {
		transition: 0.5s;
		background: linear-gradient(#e66465, #9198e5);
		/* background-color: aqua; */
	}

	#start-bubble-sort {
		margin-top: 2%;
		height: 80%;
		width: 63.5%;
	}
</style>
