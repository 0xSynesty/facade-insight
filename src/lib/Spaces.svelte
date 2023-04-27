<script>
    import Edition from './Edition.svelte'

    let spaces = {}
    export let selectedSpaceID = null
    const initSpace = (id) => {
        const name = `New space ${id}`
        return {
            name: name,
            picture: null,
            devis: null,
        }
    }

    const createNewSpace = () => {
        const id = Object.values(spaces).length
        const newSpace = initSpace(id)
        spaces[id] = newSpace
    }

    const changeName = (e, id) => {
        const name = e.detail.name
        spaces[id].name = name
    }


</script>

<div class="spaces-selection">  

<button class="new-space" on:click={createNewSpace}><em>+</em><span>New quote</button>

{#each Object.entries(spaces).reverse() as [id, space]}
    <button class="space-button" on:click={() => selectedSpaceID = id}>
        {space.name}
    </button>
{/each}
</div>
<div class="prediction">
    {#if selectedSpaceID}
    <Edition content={spaces[selectedSpaceID]} on:nameChange={(e) => changeName(e, selectedSpaceID)}/>
{/if}
</div>



<style>
.spaces-selection {
        width: 22%;
        height: 100%;
        overflow-y: scroll;
        border-radius: 15px 0 0 15px;
        background-color: rgb(208, 208, 208);
  }
  .prediction {
    width: 78%;
    height: 100%;
    overflow-y: scroll;
    background-color: #F9A828;
    border-radius: 0 15px 15px 0;
    color: white;
    
  }
  .new-space {
    height: 3em;
    width: 98%;
    border-radius: 15px;
    margin-top: 0.4em;
    margin-bottom: 0.2em;
    color: #fff;
    font-weight: 600;
    font-size: 1em;
    display: inline-flex;
    align-items: center;
    justify-content: center;
  }
  .space-button {
    /* box-sizing:border-box; */
    width: 98%;
    height: 3em;
    border-radius: 12px;
    font-size: 1.1em;
    font-weight: 500;
    background-color: #2e383f;
    margin-bottom: 0.2em;
    transition: border-color 0.5s, background-color 0.5s;
  }
  .space-button:hover {
    border-color: #F9A828;
    background-color: #F9A828;
  }
  .new-space em {
    font-size: 2em;
    margin-right: 0.3em;
    
  }
</style>