<script lang="ts">
   import { page } from "$app/stores";
   import { onMount } from "svelte";


   let songResults: any[] = []
   let errorMessage = false

   onMount(async () => {
    try {
      let searched = $page.params.searched
      const itunesSearched = await fetch(`https://itunes.apple.com/search?term=${searched}&entity=song`);
    let res = await itunesSearched.json();
    songResults = res.results;
    if (songResults.length === null || songResults.length === 0) {
      throw Error
    }
    } catch (error) {
      errorMessage = true
    } 
   })




</script>


<svelte:head>
	<title>iTunes Artist Song Search | {$page.params.searched} songs</title>
</svelte:head>

{#if errorMessage}
<h1 class="text-4xl text-center mb-12">Sorry, there are no songs listed for {$page.params.searched}</h1>
<div class="mb-7 ml-5">
  <a  href='/'>← Back to home</a>
</div>
{:else}
<h1 class="text-4xl text-center mb-4">Songs by or featuring {$page.params.searched}</h1>
<div class="mb-7 ml-5">
  <a  href='/'>← Back to home</a>
</div>     
{/if}
<div class="grid grid-cols-2 md:grid-cols-3 grod-flow row gap-3">
  {#if !errorMessage}
    {#each songResults as song}
   <a  href={`${$page.params.searched}/${song.trackId}`} class="p-3 flex bg-white rounded-md bg-opacity-20 border-2 border-white border-opacity-30">
     <img src={song.artworkUrl100} alt="img" class="rounded-md mr-4 w-1/4">
     <div class="flex flex-col items-start text-left">
       <div class="mb-2 h-6 overflow-hidden">{song.trackName}</div>
       <div class="text-xs font-bold">{song.artistName}</div>
     </div>
   </a>
   {/each}
  {/if}
  
 </div>



<style>
   
</style>