<script lang="ts">
    import { Container, Image, Button } from 'sveltestrap';
    import Carousel from 'svelte-carousel'
    import { onMount } from 'svelte';

    const image_size = 400;

    onMount(
        window.postMessage({ message: { type: 'CONNECT_HYDRAWALLET' }}, '*')
    )

    function handleHydrawalletAcctChanged(event) {
        if (event.data.message && event.data.message.type === "HYDRAWALLET_ACCOUNT_CHANGED") {
                if (event.data.message.payload.error){
                        // handle error
                }
        console.log("account:", event.data.message.payload.account)
    } 
}
window.addEventListener('message', handleHydrawalletAcctChanged, false);


  </script>

  <style>
      section, h1 {
          display: flex;
          justify-content: center;
      }
  </style>

<Container fluid>
    <h1>Mint your NFT</h1>
    

    
</Container>

  
