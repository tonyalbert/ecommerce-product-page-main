<template>
    <TheHeader :cartItems="cartItems" />
    <ProductImages /> 

    <div class="px-5 py-3">
        <span class="text-orange font-bold text-sm tracking-widest">SNEAKER COMPANY</span>
        <h1 class="my-3 text-3xl font-black	opacity-75">Fall Limited Edition Sneakers</h1>
        <p class="text-black opacity-75">These low-profile sneakers are your perfect casual wear companion. Featuring a durable rubber outer sole, they’ll withstand everything the weather can offer.</p>
     
    
        <div class="flex justify-between my-5">
            <div class="flex items-center">
                <h2 class="text-3xl font-bold opacity-75 mr-3">${{ price }}</h2>
                <span class="bg-pale-orange text-orange font-bold rounded-md px-2 py-1">50%</span>
            </div>

            <span class="text-black opacity-75 font-semibold"><s>$250.00</s></span>
        </div>

        <div class="flex justify-between my-8 items-center px-5">
            <button @click="removeItens"><img src="../assets/images/icon-minus.svg" alt=""></button>
            <span class="text-black opacity-75 text-xl font-semibold">{{ quantidy }}</span>
            <button @click="addItens"><img src="../assets/images/icon-plus.svg" alt=""></button>
        </div>

        <CartButton :buttonText="buttonText" :clickFunction="addToCart" />

    </div> 
</template>

<script>
import ProductImages from './ProductImages.vue';
import TheHeader from './TheHeader.vue'
import CartButton from './CartButton.vue';

export default {
    components: {
        ProductImages,
        TheHeader,
        CartButton
    },
    data(){
        return{
            productName: 'Fall Limited Edition Sneakers',
            price: 125,
            quantidy: 1,
            cartItems: [],
            buttonText: 'Add to cart'
        }
    },
    methods:{
        addItens(){
            this.quantidy++
            this.valor = this.quantidy * 125
        },
        removeItens(){
            if(this.quantidy > 1){
                this.quantidy--
                this.valor = this.quantidy * 125
            }   
        },
        addToCart(){
            this.cartItems.push({
                name: this.productName,
                price: this.price
            })
        }
    }
}


</script>