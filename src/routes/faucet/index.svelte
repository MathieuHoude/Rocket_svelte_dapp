<script>
    import { onMount } from 'svelte';
    import { defaultEvmStores, web3, selectedAccount, connected, chainId, chainData } from 'svelte-web3'
    import { signERC2612Permit } from 'eth-permit';
    import { Container, Image, Button } from 'sveltestrap';
    export let message
    export let tipAddress
    import RocketTokenContract from './RocketToken.json';
    const CONTRACT_ADDRESS = '0x179f3Dc36719aa51945AF484E3EeD13E7fff4ae3';

    let contractInstance;

    $: checkAccount = $selectedAccount || '0x0000000000000000000000000000000000000000'
    $: balance = $connected ? $web3.eth.getBalance(checkAccount) : ''
    const sendTip = async (e) => {
      console.log('Received move event (sendTip button)', e)
      const tx = await $web3.eth.sendTransaction({
        // gasPrice: $web3.utils.toHex($web3.utils.toWei('30', 'gwei')),
        gasLimit: $web3.utils.toHex('21000'),
        from: $selectedAccount,
        to: tipAddress,
        value: $web3.utils.toHex($web3.utils.toWei('1', 'finney'))
      })
      console.log('Receipt from sendTip transaction', tx)
      alert('Thanks!')
    }
    onMount(
      async () => {
        message = 'Connecting to Ethereum Testnet Görli...'
         await defaultEvmStores.setBrowserProvider()
        message = ''
        contractInstance = await getContract(CONTRACT_ADDRESS)
      })

    async function permit()  {
        const value = $web3.utils.toWei('1', 'ether');
        
        // Sign message using injected provider (ie Metamask).
        // You can replace window.ethereum with any other web3 provider.
        const result = await signERC2612Permit($web3.currentProvider, CONTRACT_ADDRESS, '0x49C99dB83eA1cDa354b718A4Be90f4B1C3Dc94A4', '0x642be3BA96c16a819Db48944c1e029dF55E4dC6d', value);
        console.log(result)
        await contractInstance.methods.permit('0x49C99dB83eA1cDa354b718A4Be90f4B1C3Dc94A4', '0x642be3BA96c16a819Db48944c1e029dF55E4dC6d', value, result.deadline, result.v, result.r, result.s).send({
            from: '0x49C99dB83eA1cDa354b718A4Be90f4B1C3Dc94A4',
        });
    }
    async function getContract(address) {
    const networkId = await $web3.eth.net.getId();
    const deployedNetwork = RocketTokenContract.networks[networkId];
    return new $web3.eth.Contract(
        RocketTokenContract.abi,
      deployedNetwork && deployedNetwork.address, {
        from: address,
        gas: 2000000
      }
    );
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
    <button on:click|once={permit}>
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
  </style>