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
    console.log(songResults)
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
<h1 class="text-4xl text-center mb-12">Sorry, there are no songs listed for <span class="text-[#fc8ea0]">{$page.params.searched}</span></h1>
<div class="mb-7 ml-5">
  <a  href='/'>← Back to home</a>
</div>
{:else}
<h1 class="text-4xl text-center mb-4">Songs by or featuring <span class="text-[#fc8ea0]">{$page.params.searched}</span></h1>
<div class="mb-7 ml-5">
  <a  href='/'>← Back to home</a>
</div>     
{/if}

 <div class="container px-5 mx-auto">
  <div class="flex flex-wrap -m-4">

{#if !errorMessage}
{#each songResults as song}
<div class="p-4 w-full md:w-1/2" >
<div class="h-full border-2 border-gray-200 border-opacity-60 rounded-lg overflow-hidden">
<div class="w-full">
    <div class="w-full flex p-2">
        <div class="p-2 ">
          <img 
        
           src={song.artworkUrl100} alt="img"
            class="w-10 h-10 overflow-hidden"/>
        </div>
        <div class="pl-2  ">
          <a  href={`${$page.params.searched}/${song.trackId}`} class=" text-sm">{song.trackName}</a>
          <p class="text-xs font-bold mt-1 mb-2">{song.artistName}</p>
        </div>
      </div>
</div>
</div>
</div>
{/each}
{/if}

  </div>
</div>


<style>
   
</style>

