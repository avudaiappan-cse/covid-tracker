<template>
  <div class="hello">
    <Header title="Covid Tracker" :count="cart.length"></Header>
    <div>
      <Container />
    </div>
    <Footer></Footer>
  </div>
</template>

<script>
import Header from "./MainPageHeader";
import Container from "./MainPageContainer";
import Footer from "./MainPageFooter";
export default {
  name: "MainPage",
  methods: {
    addCart: function(index) {
      this.cart.push(this.products[index]);
    }
  },
  watch: {
    addCart: function() {
      console.log("Changed");
    }
  },
  data: function() {
    return {
      cart: [],
      products: [
        {
          id: 1,
          imageURL:
            "https://rukminim1.flixcart.com/image/332/398/jmp79u80/bag/w/a/w/black-backpack-new-eva-10-original-imaf7mynrtaq3t7u.jpeg?q=50",
          productName: "Black Color Bag for Sale!",
          prevPrice: "$21",
          currPrice: "$12"
        },
        {
          id: 2,
          imageURL:
            "https://rukminim1.flixcart.com/image/332/398/jmp79u80/bag/w/a/w/black-backpack-new-eva-10-original-imaf7mynrtaq3t7u.jpeg?q=50",
          productName: "Black Color Bag for Sale!",
          prevPrice: "$21",
          currPrice: "$12"
        },
        {
          id: 3,
          imageURL:
            "https://rukminim1.flixcart.com/image/332/398/jmp79u80/bag/w/a/w/black-backpack-new-eva-10-original-imaf7mynrtaq3t7u.jpeg?q=50",
          productName: "Black Color Bag for Sale!",
          prevPrice: "$21",
          currPrice: "$12"
        },
        {
          id: 4,
          imageURL:
            "https://rukminim1.flixcart.com/image/332/398/jmp79u80/bag/w/a/w/black-backpack-new-eva-10-original-imaf7mynrtaq3t7u.jpeg?q=50",
          productName: "Black Color Bag for Sale!",
          prevPrice: "$21",
          currPrice: "$12"
        }
      ]
    };
  },
  components: {
    Header,
    Container,
    Footer
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.productsContainer {
  display: grid;
  grid-template-columns: repeat(3, auto);
  column-gap: 10rem;
}
</style>
