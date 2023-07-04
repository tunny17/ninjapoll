<script>
	import Modal from './Modal.svelte';
	import AddPersonForm from './AddPersonForm.svelte';
	
	let showModal = false;

	let people = [
		{ name: 'Ramy', beltColor: 'red', age: 25, id: 1 },
		{ name: 'Sonny', beltColor: 'blue', age: 65, id: 2 },
		{ name: 'Ahmed', beltColor: 'purple', age: 55, id: 3 },
	]

	const handleClick = (id) => {
		// delete person from people
		people = people.filter((person) => person.id != id);
	}

	const toggleModal = () => {
		showModal = !showModal;
	}

	const addPerson = (e) => {
		// console.log(e.detail);
		const person = e.detail;
		people = [person, ...people];
		showModal = false;
	}

</script>

<Modal {showModal} on:click={toggleModal}>
	<AddPersonForm on:addPerson={addPerson} />
</Modal>
<main>
	<button on:click={toggleModal}>Open Modal</button>
	{#each people as person (person.id)}
		<div>
			<h4>{person.name}</h4>
			{#if person.beltColor === 'red'}
				<p><strong>Master Ninja</strong></p>
			{:else if person.beltColor === 'blue'}
				<p><strong>Sensi</strong></p>
			{:else}
				<p><strong>Student</strong></p>
			{/if}
			<p>{person.age} years old, {person.beltColor}</p>
			{#if person.skills}
				<p>{person.skills}</p>
			{/if}
			<button on:click={() => handleClick(person.id)}>Delete</button>
		</div>
	{:else}
		<p>There are no people to show...</p>
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