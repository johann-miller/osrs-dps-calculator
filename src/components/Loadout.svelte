<script>
    let slots = [
        'helm',
    ]
    let options = [
        'option',
        'opti',
        'op',
        'o'
    ]
    let filteredOptions = options
    let equipment = ""

    function filterOptions() {
        let array = []
        let input = equipment
        input = input.toUpperCase()

        function filter(item, index) {
            let upperItem = item.toUpperCase()
            if (upperItem.includes(input)) {
                array.push(item)
            }
        }

        options.forEach(filter)
        filteredOptions = array
    }
</script>

<style>
    .loadout {
        display: flex;
        flex-flow: column;
        align-items: flex-start;
    }
</style>

<h1>Loadout</h1>

<form action="" onsubmit="event.preventDefault()" class="loadout">
    <label for="equipment">Equipment</label>
    <input type="text" id="equipment" on:keyup="{filterOptions}" bind:value="{equipment}">
    <ul>
        {#each filteredOptions as option}
            <li>{option}</li>
        {/each}
    </ul>
</form>