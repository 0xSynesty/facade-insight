<script>
    import { createEventDispatcher } from 'svelte'
    const dispatch = createEventDispatcher()

    export let content;
    let imageVisible = false;

    let estimatedWorks = [
        {
            workDesc: "Repair Steering Column",
            qty: 1,
            unit: "Assembly",
            unitCost: 480,
            amount: 480
        },
        {
            workDesc: "SpaceX Falcon Heavy Rocket (small)",
            qty: 1,
            unit: "Pc.",
            unitCost: 700000,
            amount: 700000
        },
        {
            workDesc: "Plaster 10lbs",
            qty: 10,
            unit: "Pcs.",
            unitCost: 12,
            amount: 120
        },
        {
            workDesc: "Scaffolding",
            qty: 1,
            unit: "Assembly",
            unitCost: 2000,
            amount: 2000
        }

    ]


    const handleNameChange = (e) => {
        dispatch('nameChange', { name: content.name })
        console.log(content)
    }

    const displayImage = () => {
        imageVisible = true
    }

    const downloadQuote = () => {

    }

</script>
<div class="input quote-name">
    <label for="name">Quote name</label>
    <input id="name" type="text" bind:value={content.name} on:input={(e) => handleNameChange(e)}>
</div>

<form>
    <fieldset class="customer-information">
        <legend>Customer information</legend>
        <div class="input">
            <label for="reference">Reference Number</label>
            <input id="reference" type="text">
        </div>
        <div class="input">
            <label for="customer-name">Customer Name</label>
            <input id="customer-name" type="text">
        </div>
        <div class="input">
            <label for="date">Date</label>
            <input id="date" type="date">
        </div>
        <div class="input">
            <label for="contact-person">Contact Person</label>
            <input id="contact-person" type="text">
        </div>
        <div class="input">
            <label for="contact-number">Contact Number</label>
            <input id="contact-number" type="text">
        </div>
        <div class="input">
            <label for="email">Contat email</label>
            <input id="email" type="email">
        </div>

        <div class="input wide">
            <label for="address">Address</label>
            <input id="address" type="text">
        </div>
    </fieldset>
    <div class="cost-prediction">
        <div class="image">
            <div style="margin-left: 2em">Picture of the facade</div>
            {#if !imageVisible}
                <button on:click={displayImage}>Upload image</button>
            {:else}
                <img src="src/assets/facade.jpg"/>
            {/if}
        </div>
        {#if imageVisible}
            <div class="estimated-works">
                <h1>Estimated works</h1>
                <table>
                <thead>
                    <tr>
                        <th>Work Description</th>
                        <th>Unit</th>
                        <th>Quantity</th>
                        <th>Unit costs</th>
                        <th>Amount</th>
                    </tr>
                </thead>
                    {#each estimatedWorks as element}
                    <tr>
                        <td>{element.workDesc}</td>
                        <td>{element.qty}</td>
                        <td>{element.unit}</td>
                        <td>{element.unitCost}</td>
                        <td>{element.amount}</td>
                    </tr>
                    {/each}
                <tfoot>
                    <tr>
                        <td><strong>Total</strong></td>
                        <td></td>
                        <td></td>
                        <td></td>
                        <td>702,600.00</td>
                    </tr>
                    </tfoot>
                </table>
                <a class="generate-quote" href="src/assets/quote_davidluis_export.pdf" download>Generate quote</a>
            </div>
            
        {/if}
    </div>
</form>


<style>
    .image {
        font-size: 1.5em;
        font-weight: 500;
    }
    .image button {
        height: 2em;
        border-radius: 3px;
        background-color: #333;
        margin-bottom: 1em;
    }
    .generate-quote {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 3em;
        padding: 10px;
        background-color: #333;
        margin-top: 2em;
        font-size: 1.5em;
        font-weight: 600;
        border-radius: 15px;
        transition: background-color 0.5s, border 0.5s;
    }
    .generate-quote:hover {
        background-color: #F9A828;
        border: 2px solid white;
    }
    .image img{
        max-width: 100%;
        height: auto;
        margin-right: 2em;
    }
    .quote-name {
        font-size: 1.5em;
        margin: 10px 30%;
    }
    .estimated-works {
        min-width: 4em;
        margin: 2em;
    }
    .customer-information {
        display: grid;
        align-items: center;
        justify-content: center;
        grid-template-columns: 30% 30% 30%;
        gap: 1em;
        margin: 1em;
        border-radius: 10px;
        margin-bottom: 20px;
        background-color: #febb4f;
        border: 1px solid rgb(208, 208, 208);
    }
    legend {
        font-size: 1.3em;
        font-weight: 600;
        background-color: #333;
        border-radius: 10px;
        padding: 10px;
    }
    .cost-prediction {
        display: flex;
        margin: 2em;
        background-color: #febb4f;
        border: 1px solid rgb(208, 208, 208);
        border-radius: 10px;
    }
    table {
        color: #333;
        background: white;
        border: 1px solid grey;
        font-size: 12pt;
        border-collapse: collapse;
    }
    table thead th,
    table tfoot th {
        color: black;
        background: rgba(0,0,0,.1);
    }
    table th,
    table td {
        padding: .5em;
        border: 1px solid rgb(208, 208, 208);
    }

    table tfoot td {
        color: black;
        background: rgba(0,0,0,.1);
    }

    label {
        display: block;
        font-weight: 500;
    }
    
    .wide {
        grid-column: span 3;
    }
    #address {
        width: 80%;
    }
    input {
        border-radius: 7px;
        height: 2em;
        width: 80%;
        border: 2px solid rgb(208, 208, 208);
        font-family: inherit;
    }
</style>