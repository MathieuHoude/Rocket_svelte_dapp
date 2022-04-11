<script>
	import Header from '$lib/header/Header.svelte';
	import '../app.css';
</script>

<Header />

<main>
	<slot />
</main>

    <!-- FOOTER -->
    <footer id="contact_us">
        <div class="footer-flex-wrapper">
            <div class="office-item">
                <h3>United States Office</h3>
                <p>
                    456 harlem boulevard<br> 
                    saratoga springs, ny, usa<br> 
                    <a href="tel:+19995434567">1 999 543-4567</a>                    
                </p>
            </div>
            <div class="office-item text-right">
                <h3>Canada Office</h3>
                <p>                      
                     23895 bradshaw boulevard<br> 
                     kingston, ont, ca<br> 
                    <a href="tel:+19995434567">1 999 543-4567</a>                    
                </p>
            </div>
        </div>

        <div class="footer-copyrights">
            <p>
                All rights reserved to Rocket Elevators &copy;, 2022.
            </p>            
        </div>
    </footer>

<style>
	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		/* max-width: 1024px; */
		margin: 0 auto;
		box-sizing: border-box;
	}

	/* FOOTER */
	footer {
	padding: 50px 25px;
	}

	footer .footer-flex-wrapper {
	display: flex;
	flex-shrink: 0;
	justify-content: space-between;
	align-items: center;
	padding: 25px;
	}

	footer .footer-flex-wrapper .office-item.text-right {
	text-align: right;
	}

	footer .footer-flex-wrapper .office-item h3 {
	margin-bottom: 8px;
	color: #ff7630;
	text-transform: uppercase;
	font-size: 15px;
	font-weight: 700;
	}

	footer .footer-flex-wrapper .office-item p {
	margin-top: 0;
	color: #292929;
	font-size: 22px;
	text-transform: uppercase;
	font-weight: 300;
	}

	footer .footer-flex-wrapper .office-item p a {
	color: #292929;
	font-weight: 700;
	transition: color 250ms ease;
	outline: 0;
	}

	footer .footer-flex-wrapper .office-item p a:hover,
	footer .footer-flex-wrapper .office-item p a:focus {
	color: #ff7630;
	text-decoration: underline;
	}

	footer .footer-copyrights {
	display: block;
	margin-top: 40px;
	}

	footer .footer-copyrights p {
	margin: 0;
	text-align: center;
	font-size: 12px;
	font-weight: 300;
	color: #292929;
	}

	@media (min-width: 480px) {
		footer {
			padding: 40px 0;
		}
	}
</style>
