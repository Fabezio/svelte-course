<script>
	import Product from './Product.svelte'
	import Modal from './Modal.svelte'
	let products = [
		{
			// id: "1",
			author: "Jules Verne",
			title: "Journey to the Earth Core",
			// bestseller:true,
			price: 4.95
		}
	]
	let showModal=false
		// let title
	function addToCart(e) {console.log(e.detail)}
	function deleteFromCart(e) {console.log(e.detail)}

</script>

<main>
	{#each products as product}
	<Product 
		{...product}
		on:add-to-cart={addToCart}
		on:delete={deleteFromCart}
	 />
	{/each}

	<button on:click={() => showModal = true } >show modal</button>
	{#if showModal}
	<Modal 
		on:cancel={() => showModal = false}
		on:close={() => showModal = false}
	>
		<h1 slot="header">Hello!</h1>
		<p slot="content">Good to see ya!</p>
		<!-- <button slot="footer" on:click={() => showModal = false }>Close</button> -->
	 </Modal>
	 {/if}
</main>

<style>
	main {
		/* text-align: center; */
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>