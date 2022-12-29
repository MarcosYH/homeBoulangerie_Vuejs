<template>
  <!--<nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  <router-view/>-->
  <div id="app" class="app">
		<h1>{{ restaurantName }}</h1>
		<p class="description">
			Bienvenue dans notre café {{ restaurantName }}! Nous sommes réputés pour
			notre pain et nos merveilleuses pâtisseries. Faites vous plaisir dès le
			matin ou avec un goûter réconfortant. Mais attention, vous verrez qu'il
			est difficile de s'arrêter.
		</p>

		<section class="menu">
			<h2>Menu</h2>
			<MenuItem
				v-for="item in simpleMenu"
				:addToShoppingCart="addToShoppingCart"
				:name="item.name"
				:image="item.image"
				:quantity="item.quantity"
				:inStock="item.inStock"
				:key="item.name"
			/>
		</section>

		<aside class="shopping-cart">
			<h2>Panier d'achat : {{ shoppingCart }} articles</h2>
		</aside>
    <button>COMMANDER</button>
		<h2>Contactez nous</h2>
		<p>Adresse : {{ address }}</p>
		<p>Téléphone : {{ phone }}</p>
		<p>Email : {{ email }}</p>
		<p>Horaires :</p>
			<li>L-V: 06:00 à 16:00</li>
			<li>Samedi: 07:00 à 14:00</li>
			<li>Dimanche: 07:00 à 12:00</li>
		<footer class="footer">
			<p>{{ copyright }}</p>
		</footer>
	</div>
</template>



<script>
import MenuItem from "./components/MenuItem"
export default {
	name: "App",
	components: {
		MenuItem
	},
	data() {
		return {
			address: "18 avenue du Beurre, Paris, France",
			email: "hello@cafewithavue.bakery",
			phone: "01 88 88 88 88",
			restaurantName: "La belle vue",
			shoppingCart: 0,
      qty: this.quantity,
			simpleMenu: [
				{
					name: "Croissant",
					image: {
						source: "/Image/crossiant.png",
						alt: "Un croissant"
					},
					inStock: true,
					quantity: 1
				},
				{
					name: "Baguette de pain",
					image: {
						source: "/Image/french-baguette.png",
						alt: "Quatre baguettes de pain"
					},
					inStock: true,
					quantity: 1
				},
				{
					name: "Éclair",
					image: {
						source: "/Image/eclair.png",
						alt: "Éclair au chocolat"
					},
					inStock: false,
					quantity: 1
				}
			]
		}
    
	},
	computed: {
		copyright() {
			const currentYear = new Date().getFullYear()
			return `Copyright ${this.restaurantName} ${currentYear}`
		}
	},
	methods: {
		addToShoppingCart(amount) {
			this.shoppingCart += amount
		}
    
	},

}
</script>


<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #5183b4;
  
}
body{
  background-color:rgb(238, 210, 175);
  width: 50%;
  margin: auto;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
  image-orientation: width 10vw;
}
.description {
  font-size: 18px;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  text-align: center;

}
button{
  font-size: 20px;
  outline: 0;
    background: #1eac5e;
    width: 40%;
    border:0;
    padding: 15px;
    font-size: 14px;
    transition: all 0.3 ease;
    cursor: pointer;
}

</style>
