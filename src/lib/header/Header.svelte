<script lang="ts">
	import {Image,Collapse, Navbar,NavbarToggler,NavbarBrand,Nav,NavItem,NavLink,Dropdown,DropdownToggle,DropdownMenu,DropdownItem} from 'sveltestrap/src';
  
	let isOpen = false;
  
	function handleUpdate(event) {
	  isOpen = event.detail.isOpen;
	}
  </script>
  
  <Navbar color="dark" dark expand="md">
	<NavbarBrand href="/" ><Image alt="Landscape" src="R2.png" style="max-height: 3em" /></NavbarBrand>
	<NavbarToggler on:click={() => (isOpen = !isOpen)} />
	<Collapse {isOpen} navbar expand="md" on:update={handleUpdate}>
	  <Nav class="ms-auto" navbar>
		<NavItem>
		  <NavLink href="/">Home</NavLink>
		</NavItem>
		<NavItem>
		  <NavLink href="https://github.com/bestguy/sveltestrap">Get NFT</NavLink>
		</NavItem>
		<Dropdown nav inNavbar>
		  <DropdownToggle nav caret>Collection</DropdownToggle>
		  <DropdownMenu end>
			<DropdownItem href="/">Explore</DropdownItem>
			<DropdownItem divider />
			<DropdownItem>My NFTs</DropdownItem>
		  </DropdownMenu>
		</Dropdown>
	  </Nav>
	</Collapse>
  </Navbar>