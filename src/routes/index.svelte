<script context="module">
	export const prerender = true;
</script>

<script>
	import Collection from '$lib/Collection.svelte';
	import Sponsor from '$lib/Sponsor.svelte';
	import { Col, Container, Row } from 'sveltestrap/src';
</script>

<svelte:head>
	<title>Rocket Elevators NFT</title>
	<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/css/bootstrap.min.css">
</svelte:head>
<!-- <Container fluid>
	<Row>
		<Col>

		</Col>
	</Row>
</Container> -->


	<Container fluid>
		<Sponsor/>
		<Collection/>
		
	</Container>

