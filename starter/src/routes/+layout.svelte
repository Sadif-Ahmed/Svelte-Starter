
<script>
	import '../app.postcss';

	import { DarkMode,Navbar, NavBrand, NavLi, NavUl, NavHamburger, Dropdown, DropdownItem, Chevron, DropdownDivider } from 'flowbite-svelte'
  </script>
  <DarkMode/>
  <Navbar let:hidden let:toggle>
	<NavBrand href="/">
	  <img
		src="/images/flowbite-svelte-icon-logo.svg"
		class="mr-3 h-6 sm:h-9"
		alt="Flowbite Logo"
	  />
	  <span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white">
		Flowbite
	  </span>
	</NavBrand>
	<NavHamburger on:click={toggle} />
	<NavUl {hidden}>
	  <NavLi href="/" active={true}>Home</NavLi>
	  <NavLi id="nav-menu1" class="cursor-pointer"><Chevron aligned>Dropdown</Chevron></NavLi>
	  <NavLi href="/services">Services</NavLi>
	  <NavLi href="/pricing">Pricing</NavLi>
	  <NavLi href="/contact">Contact</NavLi>
	  <Dropdown triggeredBy="#nav-menu1" class="w-44 z-20">
		<DropdownItem>Dashboard</DropdownItem>
		<DropdownItem>Settings</DropdownItem>
		<DropdownItem>Earnings</DropdownItem>
		<DropdownDivider />
		<DropdownItem>Sign out</DropdownItem>
	  </Dropdown>
	</NavUl>
  </Navbar>
<slot />
