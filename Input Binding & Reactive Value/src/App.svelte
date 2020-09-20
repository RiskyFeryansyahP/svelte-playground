<script>
	let firstName = 'Risky'
	let lastName = 'Pribadi'
	let beltColour = 'black'

	$: fullName = `${firstName} ${lastName}` // reactive values
	// reactive statement
	$: {
		console.log(beltColour)
	}

	const handleInput = (event) => {
		beltColour = event.target.value
	}
</script>

<main>
	<p style="color: {beltColour}"> {fullName} - {beltColour} color </p>
	<!-- if want to binding 1 ways, we only use on:input -->
	<!-- <input type="text" on:input={handleInput} value={beltColour}> -->

	<!-- short hand -->
	<!-- if want to binding 2 ways, we need use bind:value -->
	<input type="text" bind:value={firstName} />
	<input type="text" bind:value={lastName}>
	<input type="text" bind:value={beltColour} />
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>