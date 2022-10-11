<script lang="ts">
    import { Container, Image, Button } from 'sveltestrap';
    import Carousel from 'svelte-carousel'
    import { onMount } from 'svelte';
    import { Hydraweb3 } from 'hydraweb3-js';

    let hydraweb3, contract, account;

    const contractAddress = '487a8137404198dd6bcc162fda4626e1cc032c22';
    import HydraNFTABI from './HydraNFT.json';

    let balance = null;
    let minted = 'Please wait...'

    // $: balance = isConnected() ? $web3.eth.getBalance(checkAccount) : ''

    const image_size = 400;

    onMount( async () => {
            window.postMessage({ message: { type: 'CONNECT_HYDRAWALLET' }}, '*')
            minted = await getTotalSupply();
        }
    )

    function handleHydrawalletAcctChanged(event) {
        if (event.data.message && event.data.message.type === "HYDRAWALLET_ACCOUNT_CHANGED") {
            if (event.data.message.payload.error){
                    // handle error
            }
            console.log("account:", event.data.message.payload.account)
            if (event.data.message.payload.account.loggedIn) {
                account = event.data.message.payload.account;
                balance = event.data.message.payload.account.balance / 100000000;
            }

            hydraweb3 = new Hydraweb3(window.hydrawallet.rpcProvider);
            console.log("hydraweb3: ", hydraweb3)
            // Create a new Contract instance and use the same provider as hydraweb3
            contract = hydraweb3.Contract(contractAddress, HydraNFTABI);
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

    async function isConnected() {
        return await hydraweb3.isConnected();
    }

    async function getTotalSupply() {
        const data = hydraweb3.encoder.constructData(contract.abi, "totalSupply", []);
        let result = await contract.provider.rawCall('callcontract', [contract.address, data, account]);
        console.log("response: ", result)
        let name = hydraweb3.decoder.decodeCall(result, contract.abi, "totalSupply", true);
        console.log(name)
    }

</script>

<style>
    section, h1, h2 {
        display: flex;
        justify-content: center;
    }
</style>

<Container fluid>
    <h1>Your current balance:</h1>
    <h2>{balance}</h2>
    <h1>Total NFT minted: </h1>
    <h2>{minted}</h2>
    <button on:click={getTotalSupply}></button>

    
</Container>

  
