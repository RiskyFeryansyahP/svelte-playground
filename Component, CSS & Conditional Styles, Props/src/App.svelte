<script lang="ts">
	// importing
	import Modal from './components/Modal.svelte'

	let peoples = [
		{ id: 1, name: 'Risky Feryansyah', age: 21, belt: 'black'},
		{ id: 2, name: 'Shania Saraswati', age: 21, belt: 'yellow' },
		{ id: 3, name: 'Cindy Puspita', age:18, belt: 'red' },
	]

	const num: number = 5
	const message: string = "Hello, im a prop value"

	// delete data from peoples
	const handleClick = (e: MouseEvent, id: number) => {
		peoples = peoples.filter((people) => people.id !== id)
	}
</script>

<Modal message={message} isPromo={false} /> <!-- passing message and is promo props to modal component-->
<main>
	{#each peoples as people (people.id)}
		<div>
			<h4> Name: {people.name} </h4>
			{#if people.belt === 'black'}
				<strong> MASTER NINJA </strong>
			{/if}
			<p> {people.age} years old, {people.belt} belt. </p>
			<button on:click={(e) => handleClick(e, people.id)}> Delete </button>
		</div>
		
		{:else}
			<p> There are no people to show... </p> 
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>