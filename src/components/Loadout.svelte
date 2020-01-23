<script>
    let options = [
        'void melee helm',
        'serpentine visage',
        'archer\'s helm',
        'helm of neitiznot'
    ]
    let filteredOptions = options
    let equipment = ""
    let equipmentInput
    let showOptions = false
    let helm = ""

    function filterOptions() {
        let array = []
        let input = equipmentInput
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

    function openOptions() {
        showOptions = true
    }

    function setEquipment(value) {
        equipment = value
    }
</script>

<style>
    .loadout {
        display: flex;
        flex-flow: column;
        align-items: flex-start;
    }

    ul {
        list-style-type: none;
    }

    button {
        border: 1px #3f3e3c solid;
        background: #fcfcfc;
        color: #3f3e3c;
    }
</style>

<h1>Loadout</h1>

<ul>
    <li>
        <button on:click="{openOptions}">
            <span>Helm</span>
            <span>{equipment}</span>
        </button>
    </li>
</ul>
{#if showOptions}
<form action="" onsubmit="event.preventDefault()" class="loadout">
    <label for="equipment">Equipment</label>
    <input type="text" id="equipment" on:keyup="{filterOptions}" bind:value="{equipmentInput}" autocomplete="off">
    <ul>
        {#each filteredOptions as option}
            <li>
                <button on:click="{setEquipment(option)}">{option}</button>
            </li>
        {/each}
    </ul>
</form>
{/if}