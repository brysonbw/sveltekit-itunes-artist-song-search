<script lang="ts">
    
    import itunes from '../components/images/itunes-logo.png'
     
  </script>
  
  <div class="fixed top-0 w-full z-30 clearNav md:bg-opacity-90 transition duration-300 ease-in-out">
      <div class="flex flex-col max-w-6xl px-4 mx-auto md:items-center md:justify-between md:flex-row md:px-6 lg:px-8 bg-black">
        <div class="flex flex-row items-center justify-between p-2">
         
            <img
              
              src={itunes}
              class='borderCircle'
              height={40}
              width={40}
              alt={'itunes-logo'}
            />
          
          <p class="md:ml-2 mx-auto text-white">iTunes Artist Song Search</p>
          
        </div>
       
      </div>
    </div>
  
    <style>
       .borderCircle {
      border-radius: 9999px;
    }
    </style>