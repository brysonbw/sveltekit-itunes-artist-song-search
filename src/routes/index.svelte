<script lang="ts">
    import itunes from '../components/images/itunes-logo.png'
    import { goto } from "$app/navigation";

    let searched: string = ''
    function search (){
        if (searched == '' ||  undefined) {
            alert('please enter an artist name')
        } else {
            goto(`${searched}`)
        }
    }  

</script>


<svelte:head>
	<title>iTunes Artist Song Search | Home</title>
</svelte:head>


<div class="text-center items-center justify-center flex flex-col">

    <img       
    src={itunes}
      class='borderCircle mx-auto mb-3 animate-bounce'
      height={144}
      width={144}
      alt='itunes-logo'
    />

    <!---Title text--->
    <h1 class="text-2xl white">Search Artist Songs</h1>
    <div class="">
     <!----Search --->
     <div  class="m-4  flex">
       <input bind:value={searched}  class="rounded-l-lg p-4 border-t mr-0 border-b border-l text-gray-800 border-gray-200 bg-white w-full" placeholder="Enter artist name"/>
       <button on:click|preventDefault={search} class="md:px-8 rounded-r-lg bg-[#fc8ea0]  text-black font-bold p-4 uppercase  border-b border-r">Search</button>
   </div>

 </div>
</div>

<style>
   .borderCircle {
    border-radius: 9999px;
  }
</style>