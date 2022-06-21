<script lang="ts" context="module">
    export async function load({params}: any) {
      var songId = params.songId;
      const itunesSearched = await fetch(`https://itunes.apple.com/search?term=${songId}&entity=song`);
      var res = await itunesSearched.json();
      var songResults = res.results[0];
      return {props: {songResults}}
    }
  </script>
  <script lang="ts">
    import { page } from "$app/stores";

    type Song = {
        trackName?: string,
        artworkUrl100?: string,
        previewUrl?: string
    }
    export let songResults: Song;
  
    const prevUrl = $page.url.pathname.split('/')

  </script>

<svelte:head>
	<title>iTunes Artist Song Search | {songResults?.trackName}</title>
</svelte:head>
  
  <section>
    <div class="mt-12 flex flex-col items-center justify-center">
      <h1 class="text-3xl font-bold text-center mb-12">{songResults?.trackName}</h1>
      <img  src={songResults?.artworkUrl100} alt="img" class="w-1/4 rounded-md mb-12">
      <audio controls>
        <source src={songResults?.previewUrl} type="audio/mpeg">
      </audio>
    </div>
  </section>

  <div style="margin: 3rem 0 0;">
         
    <a href={`/${prevUrl[1]}`}>← Back</a>
  
  </div>
  
  <style>

  </style>