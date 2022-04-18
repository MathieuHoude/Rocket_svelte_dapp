<script context="module">
	export const prerender = true;
</script>

<script>
	import Gallery from '$lib/Gallery.svelte';
	import Sponsor from '$lib/Sponsor.svelte';
	import { Col, Container, Row, Button } from 'sveltestrap/src';
</script>

<style>
	    h2, h3 {
        display: flex;
        justify-content: center;
    }
	section {
        background-color: #f07171;
        padding: 5em 0 0;

    }
	section div#get-nft{
        display: flex;
        justify-content: center;
        padding-top: 2em;
    } 

</style>

<Container fluid>
	<Sponsor/>
	<section id="collection">

		<h2>Our collection</h2>
		<h3>Each NFT minted is unique, and represents a piece of Rocket Elevators history.</h3>
		<Gallery/>
		<div id="get-nft">
			<Button dark block href="/mint" style="padding: 1em 0; font-size: 3em">Get my NFT</Button>
		</div>
	
	
	</section>
	
</Container>

