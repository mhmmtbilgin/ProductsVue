<template>
<section class="container" id="container" >
	<div v-for="product in products" :key="product.id" class="product" template="groups" >
        <div class="product__favorite-box">
				<img class="product__favorite product__favorite--active" src="./assets/svg/favori.svg" />
		    </div>
        <div class="product__image" id="photo">
           <img :src="product.image" alt="Product Image" class="product__photo" >
        </div>
        <aside class="product__description">
            <h2 class="product__card-title" :title="product.title">{{product.title}}</h2>
            <p class="product__category" >{{product.category}}</p>
            <div class="product__price-box">
                <p class="product__price product__price--discount">{{product.price}} $</p>
            </div>
            <div class="product__button">
                <input type="button" class="product__add-cart" value="Sepete Ekle" >
            </div>
        </aside>
</div>
</section>

</template>

<script>
export default {
  data() {
    return {
    products :null,
    }
  },
   mounted() {
            fetch('https://fakestoreapi.com/products')
            .then(res=>res.json())
            .then(data=>this.products=data)  
    }
}
</script>

<style lang="scss">
.container{
    font-family: $font-family;
	display: flex;
	flex-direction: row;
    justify-content: center;
	flex-wrap: wrap;
}
.product{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-left: 15px;
    margin-top: 30px;
    margin-bottom: 30px;
    min-width: 285px;
    min-height: 500px;
    border-radius:6px;
    cursor:pointer;
    &:hover{
        box-shadow:$product-hover;    
    }
	&__image{
		display: flex;
		flex-direction: column;
		justify-content: center;
		margin-top: 38px;
	}
    &__favorite-box {
        display: flex;
        flex-direction: row;
        justify-content: flex-end;
        min-width: 270px;
	}
    &__favorite {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 22px;
    height: 19px;
    padding: 10px;
    opacity: 1;
    border: 1px solid $fav-border-color;
    border-radius: 50%;
     &:hover{
            background-color: $fav-hover-bgcolor;
            border:1px solid $fav-hover-border-color;
            cursor: pointer;
        }
	}	
    &__photo{
        max-width: 150px;
        height: 200px;
       
    }
	&__description{
        flex-direction: column;
        align-items: center;
        justify-content: center;
        margin-left: 16px;
	}
	&__card-title{
        color: $card-title-color;
        @include font-size(16);
        line-height: 18px;
        max-width: 200px;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;

	}
	&__category {
		display: flex;
		flex-direction: row;
		justify-content: center;
		@include font-size(16);
		color: $summary-color;
		margin: auto;
		line-height: 30px;
	}
	&__price-box{
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
	}
	&__price{
		&--discount{
			font-weight: 600;
		}
		&--nodiscount{
			font-weight: 400;
			margin-left: 20px;
			color: $nodiscount-color;
			text-decoration: line-through;
		}
	}
	&__button{
		display: flex;
		flex-direction: row;
		justify-content: center;
	}
	&__add-cart{
		width: 180px;
		height: 40px;
		margin: 10px 0 30px 0;
		border: none;
		background-color: $add-cart-bgcolor;
		color: $btn-txt-color;
		@include font-size(16);
		font-weight: 400;
        border-radius: 6px;
        &:hover{
            cursor:pointer;
            background-color: $add-cart-hover;
        }
	}
}

</style>