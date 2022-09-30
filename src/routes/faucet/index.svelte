<!-- <script>
    import { signERC2612Permit } from 'eth-permit';
    import { Container, Image, Button } from 'sveltestrap';
    export let message
    
    import { onMount } from 'svelte';
    import { defaultEvmStores, web3, selectedAccount, connected, chainId, chainData } from 'svelte-web3'
    import RocketTokenContract from './RocketToken.json';
    const NFTCONTRACT_ADDRESS = '0x5E2bB780fE31C097aF60A2D5B35726F102a75049';

    let contractInstance;

    $: checkAccount = $selectedAccount || '0x0000000000000000000000000000000000000000'
    $: balance = $connected ? $web3.eth.getBalance(checkAccount) : ''
    onMount(
      async () => {
        message = 'Connecting to Rocket Elevators blockchain...'
         await defaultEvmStores.setProvider()
        message = ''
        contractInstance = await getContract(NFTCONTRACT_ADDRESS)
        console.log(contractInstance)
      })
    const getWalletTokens = async (e) => {
      const res = await fetch(`https://express-api.codeboxxtest.xyz/NFT/getWalletTokens/${checkAccount}`, {
        method: 'GET'
      })
      const json = await res.json()
      console.log(json)
    }

    async function approve()  {
        await contractInstance.methods.approve(NFTCONTRACT_ADDRESS, 1).send({
            from: $selectedAccount,
        });
    }
    async function getContract(address) {
      const networkId = await $web3.eth.net.getId();
      console.log(networkId)
      const deployedNetwork = RocketTokenContract.networks[networkId];
      return new $web3.eth.Contract(
          RocketTokenContract.abi,
        "0x2f679c4fA4Fe7c1cB62D6fFbdC9879D3e221C93b", {
          from: address,
          gas: 2000000
        }
      );
    }
    async function permit()  {
        const value = $web3.utils.toWei('1', 'ether');
        
        // Sign message using injected provider (ie Metamask).
        // You can replace window.ethereum with any other web3 provider.
        const result = await signERC2612Permit($web3.currentProvider, NFTCONTRACT_ADDRESS, '0x49C99dB83eA1cDa354b718A4Be90f4B1C3Dc94A4', '0x642be3BA96c16a819Db48944c1e029dF55E4dC6d', value);
        console.log(result)
        // await contractInstance.methods.permit('0x49C99dB83eA1cDa354b718A4Be90f4B1C3Dc94A4', '0x642be3BA96c16a819Db48944c1e029dF55E4dC6d', value, result.deadline, result.v, result.r, result.s).send({
        //     from: '0x49C99dB83eA1cDa354b718A4Be90f4B1C3Dc94A4',
        // });
    }
  </script>
  
  <svelte:head>
      <title>svelte-web3 test</title>
  </svelte:head>
  
  <main>
  
    <p>Visit the <a href="https://web3js.readthedocs.io/en/">Web3.js documentation</a> to learn how to use Web3.js library.</p>
  
    <p>{message}</p>
  
  
    {#if $connected}
    <p>
      Connected chain: chainId = {$chainId}
    </p>
    <p>
      chainData = {JSON.stringify($chainData)}
    </p>
    <p>
      Selected account: {$selectedAccount || 'not defined'}
    </p>
  
    <p>
      {checkAccount} Balance on {$chainData.name}:
      {#await balance}
      <span>waiting...</span>
      {:then value}
      <span>{value}</span>
      {/await} {$chainData.nativeCurrency.symbol}
    </p>
    {/if}
    <button on:click={approve}>
        Click me
    </button>
  
  </main>
  
  <style>
      main {
          text-align: center;
          padding: 1em;
          max-width: 240px;
          margin: 0 auto;
      }
      h1 {
          color: #ff3e00;
          text-transform: uppercase;
          font-size: 4em;
          font-weight: 100;
      }
      @media (min-width: 640px) {
          main {
              max-width: none;
          }
      }
  </style> -->