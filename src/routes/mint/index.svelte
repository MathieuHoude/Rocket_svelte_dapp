<script lang="ts">
    import { Container, Image, Button } from 'sveltestrap';
    import Carousel from 'svelte-carousel'
    import { onMount } from 'svelte';
    import { Hydraweb3 } from 'hydraweb3-js';

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
            const hydraweb3 = new Hydraweb3(window.hydrawallet.rpcProvider);
            console.log("hydraweb3: ", hydraweb3)
        } 
    }
    function handleHydrawalletInstalledOrUpdated(event) {
        if (event.data.message && event.data.message.type === 'HYDRAWALLET_INSTALLED_OR_UPDATED') {
        // Refresh the page
        window.location.reload()
        }
    }
    window.addEventListener('message', handleHydrawalletInstalledOrUpdated, false);
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

  
