<script lang="ts">
    // importing
    import { createEventDispatcher } from 'svelte'

    let name: string
    let age: number
    let beltColor: string
    let fighting: boolean
    let sneaking: boolean
    let running: boolean
    let skills = []

    const dispatch = createEventDispatcher()

    const handleSubmitForm = () => {
        console.log(name, beltColor, age, skills)
        
        const person = {
            name: name,
            age: age,
            belt: beltColor,
            id: Math.random(),
        }

        dispatch('addPerson', person)
	}
</script>

<h3> Add a New Person </h3> <!-- add slot with specific name -->
<form on:submit|preventDefault={handleSubmitForm}>
    <input type="text" placeholder="name" bind:value={name} />
    <input type="number" placeholder="age" bind:value={age} />
    <label> Skills: </label>
    <!-- <input type="checkbox" bind:checked={fighting} /> Fighting <br />
    <input type="checkbox" bind:checked={sneaking} /> Sneaking <br />
    <input type="checkbox" bind:checked={running} /> Running <br /> -->
    <input type="checkbox" bind:group={skills} value="fighting" /> Fighting <br />
    <input type="checkbox" bind:group={skills} value="sneaking"  /> Sneaking <br />
    <input type="checkbox" bind:group={skills} value="running"  /> Running <br />
    <label> Belt Color: </label>
    <select bind:value={beltColor}>
        <option value="white">White</option>
        <option value="red">Red</option>
        <option value="yellow">Yellow</option>
        <option value="blue">Blue</option>
        <option value="black">Black</option>
    </select>
    <button> Add Person </button>
</form>

<style>

</style>