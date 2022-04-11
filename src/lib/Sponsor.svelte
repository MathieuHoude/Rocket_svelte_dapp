<script>
    import { Col, Figure, Image, Row, TabContent, TabPane } from 'sveltestrap/src';
  </script>

  <style>

section {
  padding-left: 50px;
  padding-right: 50px;
}

section .section-flex-reversed {
  display: flex;
  flex-direction: row-reverse;
  justify-content: center;
  align-items: flex-start;
}

section .section-flex-reversed .section-item {
  width: 50%;
}

section .section-content {
  padding-right: 50px;
}

section .section-content h2 {
  margin-top: 25px;
  font-size: 35px;
  font-weight: 900;
  text-transform: uppercase;
  color: #292929;
}

section .section-content h2 span {
  display: block;
  font-size: 25px;
  font-weight: 700;
}

section .section-content p {
  font-size: 20px;
  font-weight: 400;
}
  </style>

<section id="sponsor">
    <div class="section-flex-reversed">
        <div class="section-item">
            <picture>     
    
                <Figure caption="Latest elevator incident">
                    <source srcset="accident.webp" type="image/webp">     
                    <!-- <source srcset="elevator-accident-395.jpg" type="image/jpeg">  -->
                    <Image fluid alt="Elevator Accident" src="accident.webp" />
                </Figure>
             </picture>                    
        </div>
        <div class="section-item section-content">
            <h2>
                <span>Rocket Elevators</span>
                Proud to sponsor the Elevators without Borders Foundation
            </h2>
            <p>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vulputate diam placerat a et pulvinar sapien orci mauris platea. Consectetur non adipiscing duis quis leo integer adipiscing elit. Felis, cursus aenean at egestas mauris. Senectus pharetra volutpat ligula ac et. Morbi amet dignissim ipsum, in accumsan. Rhoncus in erat consectetur mi consectetur. At faucibus pellentesque et aliquet mauris. Senectus facilisi at elementum lectus non egestas. In elementum cum suspendisse quam. Congue sagittis fermentum mauris fermentum ut lectus parturient faucibus id.
            </p>
        </div>                
    </div>
</section>