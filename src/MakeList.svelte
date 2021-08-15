<script>
    export let info;
	export let myLists;

    let editMod = false;
    let saveTitle = '';

    function edit() {
        editMod = true;
        saveTitle = info.title;
    }

    function updateList() {
        info.title = saveTitle;
        $myLists = $myLists;
        editEnd();
    }
    function editEnd() {
        editMod = false;
    }

    function del() {
        $myLists = $myLists.filter(val=>{return val.bid !== info.bid;});
        console.log($myLists)
    }
</script>

{#if editMod}
<div>
    <input bind:value={saveTitle} type="text" 
    on:keydown={
        (e) => {
            e.key === 'Enter' && updateList();
        }
    }/>
    <button on:click={updateList}>Update</button>
    <button on:click={editEnd}>Cancel</button>
</div>
{:else}
<div>
    {info.title}
    <button on:click={edit}>edit</button>
    <button on:click={del}>delete</button>
</div>
{/if}

