<script>
export default {
	name: "MenuItem",
	props: ["addToShoppingCart", "image", "inStock", "name", "quantity"]

}
</script>

<template>
	<div class="menu-item">
		<div>
			<h3>{{ name }}</h3>
			<p v-if="inStock">En stock</p>
			<p v-else>En rupture de stock</p>
			<div>
                 <h1 class="img"><img class="menu-item__image" :src="image.source" :alt="image.alt" /></h1>
				<label>Quantité : </label>
				<input v-model.number="qty" id="add-item-quantity" type="number" />
				<button @click="addToShoppingCart(qty)">
					Ajouter au panier
				</button>
               
			</div>
		</div>
	</div>
</template>

<style scoped lang="scss">
img {
width: 500px;
height: 200px;
}
input{
    outline: 0;
    width: 60%;
    border: 0;
    margin: 0 0 15px;
    padding: 15px;
    box-sizing: border-box;
    font-size: 14px;
}
button{
    outline: 0;
    background: #4caf54;
    width: 30%;
    border:0;
    padding: 15px;
    font-size: 14px;
    transition: all 0.3 ease;
    cursor: pointer;

}

</style>