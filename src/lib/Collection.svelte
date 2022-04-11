
<script lang="ts">
    import { Image, Button } from 'sveltestrap';
    let image_size = 300;
</script>
<style>
    

    section {
        background-color: #f07171;
        padding: 5em 0 0;

    }

    section div#get-nft{
        display: flex;
        justify-content: center;
        padding-top: 2em;
    } 

    h2, h3 {
        display: flex;
        justify-content: center;
    }

    section div#gallery {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        padding: 3em;
    }
    
</style>

<section id="collection">
    
    <h2>Our collection</h2>
    <h3>Each NFT minted is unique, and represents a piece of Rocket Elevators history.</h3>
    <div id="gallery">
        <Image thumbnail alt="Dunes" src="https://picsum.photos/{image_size}?random=1" />

        <Image thumbnail alt="Bicycle" src="https://picsum.photos/{image_size}?random=2" />
    
        <Image thumbnail alt="Dunes" src="https://picsum.photos/{image_size}?random=3" />
    
        <Image thumbnail alt="Bicycle" src="https://picsum.photos/{image_size}?random=4" />
    
        <Image thumbnail alt="Bicycle" src="https://picsum.photos/{image_size}?random=5" />
    </div>
    <div id="get-nft">
        <Button dark block href="/" style="padding: 1em 0; font-size: 3em">Get my NFT</Button>
    </div>


</section>
