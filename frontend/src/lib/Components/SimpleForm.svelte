<script lang="ts">

    export let value = "";
    export let onSubmit:(value:string)=>void;
    export let buttonText = "Submit" //or could put children inside the button so you can write the text like an html element



    function handleSubmit(e){
        onSubmit(value)
        value = ""
    }

    //I would dispatch a svelte event but the typescript is bugged out right now so i just won't
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" bind:value={value} >
    <button class="small-button" type="submit">
        {buttonText}
    </button>
</form>

<style>
    .small-button {
        padding: 1px 8px;
        font-weight: inherit;
        margin:0;
        text-align: center;
        display: inline;
    }

    input {
        vertical-align:baseline;
        font-size: inherit;
        /* width:100%; */
        flex-grow: 1;
        padding-left: .3rem;
        padding-right: .3rem;
    }

    form {
        display:flex;
        flex-wrap: wrap;
        gap: .3rem;
        justify-content: stretch;
    }
</style>