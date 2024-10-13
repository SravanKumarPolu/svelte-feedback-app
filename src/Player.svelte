<script>
  import { createEventDispatcher} from "svelte"
  const dispatch=createEventDispatcher();
export let name;
export let points;
let showControls=false;
const addPoint=()=>(points +=1);
const removePoint=()=>(points-=1);
const toggleControls=()=>(showControls = !showControls)
const onDelete=()=>dispatch("removeplayer",name);
</script>


<div class="card">

	<h1> 
		{name.toUpperCase()}
	<button class="btn btn-sm" on:click={toggleControls}>
		{#if showControls}-{:else}+{/if} 
	</button>
  <button class="btn btn-dander btn-sm" on:click={onDelete}>X</button>
	</h1>
	<p>Points:{points}</p>
   {#if showControls}
	<button class="btn" on:click={addPoint}>+1</button>
	<button class="btn btn-dark" on:click={removePoint}>-1</button>
	 <input type="number" bind:value={points} />
	  {/if}
</div>

 
<style>


	h1 {
		color: #ff3e00;
	
	}
p{
	margin-bottom: 10px;
}
</style>