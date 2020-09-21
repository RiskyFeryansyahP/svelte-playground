<script lang="ts">
	// importing
	import Modal from './components/Modal.svelte'
import AddPersonForm from './forms/AddPersonForm.svelte'
	import AddFormPerson from './forms/AddPersonForm.svelte'

	const num: number = 5
	const message: string = "Hello, im a prop value"
	let isShowModal: boolean = false
	let name: string
	let beltColor: string
	let age: number
	// let fighting: boolean
	// let sneaking: boolean
	// let running: boolean

	let peoples = [
		{ id: 1, name: 'Risky Feryansyah', age: 21, belt: 'black'},
		{ id: 2, name: 'Shania Saraswati', age: 21, belt: 'yellow' },
		{ id: 3, name: 'Cindy Puspita', age:18, belt: 'red' },
	]

	/**
	 * event handler
	*/

	// delete data from peoples
	const handleClick = (e: MouseEvent, id: number) => {
		peoples = peoples.filter((people) => people.id !== id)
	}

	const handleToogle = () => {
		isShowModal = !isShowModal
	}

	const addPerson = (event: CustomEvent) => {
		console.log(event.detail)

		peoples = [...peoples, event.detail]
	}
</script>

<!-- 
	passing message, isPromo and isShowModal props to Modal component
	passing event handleToogle into Modal component using on:click={handleToogle}
	where the Modal component only using on:click to use handle from this root component

	{isShowModal} is shorthand to passing props if the name is same

	event modifiers:
	self — only trigger handler if event.target is the element itself
-->
<Modal isPromo={false} {isShowModal} on:click={handleToogle}>
	<!-- <h3 slot="title"> Add a New Person </h3> add slot with specific name -->
	<AddPersonForm on:addPerson={addPerson} />
</Modal> 
<main>
	<button on:click={handleToogle}> Show Modal </button>
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