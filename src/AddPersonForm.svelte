<script>
    import { createEventDispatcher } from "svelte";
    
    let dispatch = createEventDispatcher();
    
    let age;
    let name;
    let beltColor;
    let skills = [];

    const handleSubmit = () => {
        const person = {
            name,
            beltColor,
            age, 
            skills,
            id: Math.random(),
        };
        dispatch('addPerson', person);
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="name" bind:value={name}>
    <input type="number" placeholder="Age" bind:value={age}>
    <label for=''>Skills:</label>
    <input type="checkbox" bind:group={skills} value="fighting">Fighting<br>
    <input type="checkbox" bind:group={skills} value="sneaking">Sneaking<br>
    <input type="checkbox" bind:group={skills} value="running">Running<br>
    <label for="">Belt Color</label>
    <select bind:value={beltColor}>
        <option value="black">black</option>
        <option value="orange">orange</option>
        <option value="red">red</option>
        <option value="brown">brown</option>
    </select>
    <button>Add Person</button>
</form>

<style>

</style>