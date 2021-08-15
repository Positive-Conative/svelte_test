<script>
	import {writable} from 'svelte/store';
	import List from './MakeList.svelte';

	let title = '';
	let myLists = writable([]);
	let bid = 0;

	function createList() {
		if (!title.trim()) {
			title = ''
			return
		}
		$myLists.push({
			bid,
			title
		});
		$myLists = $myLists;	// 자기 자신 할당
		title = '';
		bid++;
	}
</script>

<!-- for -->
{#each $myLists as info}
	<!-- stroe 통째로 넘겨야 하기 때문에 $로 넘기면 안 됨 -->
	<List {myLists} {info}/>
{/each}


<!-- title로 연결 -->
<input bind:value={title} type="text" 
	on:keydown={
		(e)=>{e.key === 'Enter' && createList()
	}
}/>

<button on:click={createList}>
	Create list
</button>