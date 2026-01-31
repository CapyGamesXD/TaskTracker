<script>
	import { onMount } from 'svelte';

	let points = Number();
	let add = Number(0);
	function update() {
		points += add;
		add = 0;
		localStorage.setItem('points', points.toString());
		console.log('Saved!');
	}

	function plusAdd() {
		add += 5;
	}

	function subtractAdd() {
		add -= 5;
	}

	function clear() {
		points = 0;
		localStorage.setItem('points', points.toString());
	}

	onMount(() => {
		let storedpoints = Number(localStorage.getItem('points'));
		points = storedpoints;
		setInterval(() => {
			update();
		}, 120000);
	});
</script>

<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" />
<link
	href="https://fonts.googleapis.com/css2?family=BBH+Bogle&family=Quicksand:wght@300..700&display=swap"
	rel="stylesheet"
/>

<div class="centerdiv">
	<h1>Task Tracker</h1>

	<p class="points">{points}</p>
	<h2>Points</h2>
	<div class="row">
		<button on:click={subtractAdd} class="smallbutton">-</button>
		<p class="addtext">{add}</p>
		<button on:click={plusAdd} class="smallbutton">+</button>
	</div>

	<button on:click={update}>Add</button>
	<button
		on:click={() => {
			points += 10;
		}}>+10</button
	>
	<button
		on:click={() => {
			points += 20;
		}}>+20</button
	>
	<button
		on:click={() => {
			points += 30;
		}}>+30</button
	>

	<div class="divider"></div>
	<a href="info"> Info Page </a>
	<button on:click={clear}>Reset Points</button>
</div>
