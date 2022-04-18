
<script lang="ts">
    import { Image, Button } from 'sveltestrap';
    import Carousel from 'svelte-carousel'
    let image_size = 300;
</script>
<style>
    
    section {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        padding: 3em;
    }

    div {
        display: flex;
        justify-content: space-evenly;
    }
    
</style>

<section id="gallery">
    <svelte:component this={Carousel}  infinite autoplay particlesToShow={5} particlesToScroll={2}>
        {#each {length: 10} as _, index}
        <div>
            <Image thumbnail alt="NFT #{index+1}" src="https://picsum.photos/{image_size+100}/{image_size}?random={index+1}"/>
        </div>
        {/each}
    </svelte:component>
</section>
