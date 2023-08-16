<template>
    <header class="flex justify-between py-5 px-6 lg:px-24 relative">
        <div class="flex relative items-center align-center">
            <img class="mr-4 lg:hidden" src="../assets/images/icon-menu.svg" alt="menu">
            <img class="w-32 lg:w-48" src="../assets/images/logo.svg" alt="logo">
            <ul class="hidden lg:flex ml-16 text-md opacity-60 space-x-5">
                <li><a href="">Colletion</a></li>
                <li><a href="">Men</a></li>
                <li><a href="">Women</a></li>
                <li><a href="">About</a></li>
                <li><a href="">Contact</a></li>
            </ul>
        </div>

        <div class="flex items-center">
            <button @click="showMiniCart = !showMiniCart"><img class="mr-4 lg:w-7" src="../assets/images/icon-cart.svg" alt="cart"></button>
            <div class="relative">
                <div v-if="cartItems.length > 0" class="absolute bg-orange -left-8 -top-1 py-[1px] px-2 rounded-full flex items-center">
                    <span class="text-white text-[8px] font-bold">{{ cartItems.length }}</span>
                </div>
                <img class="w-6 lg:w-12 lg:ml-8 hover:border border-orange rounded-full" src="../assets/images/image-avatar.png" alt="avatar">
            </div>
        </div>  

        <div v-show="showMiniCart" class="w-11/12 bg-white items-center shadow-md lg:shadow-2xl lg:w-96 rounded-md absolute left-[15px] lg:-left[15px] lg:right-[15px] bottom-[-290px] z-50">
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
                        <button @click="removeItens"><img src="../assets/images/icon-delete.svg" alt=""></button>
                    </div>
                    <CartButton :buttonText="buttonText" :clickFunction="removeItens" />
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
            this.$emit('removeItens')
            console.log('removeItens')
        }
    }
}
</script>