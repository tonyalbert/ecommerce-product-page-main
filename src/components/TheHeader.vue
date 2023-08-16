<template>
    <header class="flex justify-between py-5 px-6 relative">
        <div class="flex relative items-center align-center">
            <img class="mr-4" src="../assets/images/icon-menu.svg" alt="menu">
            <img src="../assets/images/logo.svg" alt="logo">
        </div>

        <div class="flex items-center">
            <button @click="showMiniCart = !showMiniCart"><img class="mr-4" src="../assets/images/icon-cart.svg" alt="cart"></button>
            <img class="w-6" src="../assets/images/image-avatar.png" alt="avatar">
        </div>  

        <div v-show="showMiniCart" class="w-11/12 bg-white items-center rounded-md absolute left-[15px] bottom-[-290px] z-50">
            <p class="px-5 py-3 font-bold text-sm">Cart</p>
            <div class="h-[240px] flex flex-col border-t-2 px-5">
                <p v-if="cartItems.length === 0" class="mx-auto my-auto font-bold opacity-75">Your cart is empty</p>
                <div v-if="cartItems.length > 0" class="block my-auto space-y-6">
                    <div class="flex justify-between items-center w-full">
                        <div class="flex">
                            <img class="w-12 h-12 rounded-md mr-5 object-cover" :src="imageProductThumbnail1" alt="">
                            <div class="block">
                                <p class="opacity-75 font-medium">{{ cartItems[0].name }}</p>
                                <span class="opacity-75">${{ cartItems[0].price }} x {{ cartItems.length }} <span class="font-bold ml-2">${{ cartItems[0].price * cartItems.length }}</span></span>
                            </div>
                        </div>
                        <button @clock="removeItens"><img src="../assets/images/icon-delete.svg" alt=""></button>
                    </div>
                    <CartButton :buttonText="buttonText" :clickFunction="fim" />
                </div>
            </div>
        </div>

    </header>
</template>

<script>
import imageProductThumbnail1 from '../assets/images/image-product-1-thumbnail.jpg'
import CartButton from './CartButton.vue';

export default {
    components: { CartButton },
    props: ['cartItems'],
    data(){
        return {
            showMiniCart: false,
            imageProductThumbnail1,
            buttonText: 'Checkout',
        }
    },
    methods: {
        fim() {
            console.log('fim')
        },
        removeItens() {
            this.cartItems = []
            console.log(this.cartItems)
            console.log('removeItens')
        }
    }
}
</script>