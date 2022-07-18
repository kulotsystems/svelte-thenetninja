<script>
    let name;
    let beltColour;
    let age;

    // let fighting = false;
    // let sneaking = false;
    // let running = false;

    let skills = [];

    const handleSubmit = () => {
        console.log(name, beltColour, age);
        console.log(skills);
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input
        type="text"
        placeholder="name"
        bind:value={name}
    />
    <input
        type="number"
        placeholder="age"
        bind:value={age}
    />
    <label>Skills</label>
    <!--<label><input type="checkbox" bind:checked={fighting}></label> fighting <br>-->
    <!--<label><input type="checkbox" bind:checked={sneaking}></label> sneaking <br>-->
    <!--<label><input type="checkbox" bind:checked={running}></label>  running  <br>-->

    <label><input type="checkbox" bind:group={skills} value="fighting"></label> fighting <br>
    <label><input type="checkbox" bind:group={skills} value="sneaking"></label> sneaking <br>
    <label><input type="checkbox" bind:group={skills} value="running"></label>  running  <br>

    <label>Belt colour:</label>
    <select bind:value={beltColour}>
        <option value="black">black</option>
        <option value="orange">orange</option>
        <option value="brown">brown</option>
        <option value="white">white</option>
    </select>
    <button>Add Person</button>
</form>


<style>

</style>