<script lang="js">
    import { logged } from '../stores'
    
    const logUser = () =>  {
        $logged = true
    }
    const delogUser = () =>  {
        $logged = false
    }
</script>

<div class="topbar">
   <button on:click={delogUser} class="title">FacadeInsight</button>
    <button class="dashboard-button" on:click={logUser}>Dashboard</button>
</div>


<style>
    .topbar {
        display: flex;
        width: 100%;
        justify-content: space-between;
        padding: 15px 0;
        background: #2E383F;
        box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
        border-radius: 0px 0px 22px 22px;
        margin-bottom: 2em;
    }

    .title {
        background: none;
        border: none;
        cursor: pointer;
        margin-left: 15px;
        font-family: 'Arial';
        font-weight: 600;
        font-size: 2.2em;
        display: flex;
        align-items: center;
        color: #FFFFFF;
    }

    .title:focus {
        outline: none;
    }

    /* .dashboard-button:hover {
        font-weight: bold;
    } */
    /* .dashboard-button:focus {
        outline: none;
    } */
    .dashboard-button {
        float: right;
        width: 160px;
        margin-right: 15px;
        padding: 10px 0;
        font-size: 1.5em;
        border-radius: 15px;
        font-weight: 500;
        font-family: inherit;
    }


</style>

