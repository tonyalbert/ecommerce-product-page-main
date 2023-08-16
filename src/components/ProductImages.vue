<template>
    <div class="relative">
        <button @click="previousImage" class="lg:hidden bg-white px-4 py-3 rounded-full absolute bottom-1/2 left-4 focus:outline-none">
            <img class="" src="../assets/images/icon-previous.svg" alt="">
        </button>

        <div>
            <img class="w-full h-80 lg:h-[34rem] lg:rounded-xl object-cover" :src="currentImage" alt="">
            <div class="hidden lg:flex justify-between mt-10">
                <img class="w-28 h-28 rounded-xl hover:border-[3px]	border-orange hover:opacity-60" src="../assets/images/image-product-1-thumbnail.jpg" alt="">
                <img class="w-28 h-28 rounded-xl hover:border-[3px]	border-orange hover:opacity-60" src="../assets/images/image-product-2-thumbnail.jpg" alt="">
                <img class="w-28 h-28 rounded-xl hover:border-[3px]	border-orange hover:opacity-60" src="../assets/images/image-product-3-thumbnail.jpg" alt="">
                <img class="w-28 h-28 rounded-xl hover:border-[3px]	border-orange hover:opacity-60" src="../assets/images/image-product-4-thumbnail.jpg" alt="">
            </div>
        </div>


        <button @click="nextImage" class="lg:hidden bg-white px-4 py-3 rounded-full absolute bottom-1/2 right-4 focus:outline-none">
            <img src="../assets/images/icon-next.svg" alt="">
        </button>
    </div>
</template>

<script>
import imageProduct1 from '../assets/images/image-product-1.jpg';
import imageProduct2 from '../assets/images/image-product-2.jpg';
import imageProduct3 from '../assets/images/image-product-3.jpg';

export default {
    data(){
        return{
           images: [imageProduct1, imageProduct2, imageProduct3],
           imageIndex: 0
        }
   },
   computed:{
    currentImage(){
        return this.images[this.imageIndex]
    }
   },
   methods:{
    nextImage(){
        var lengt = this.images.length
        if(this.imageIndex < lengt - 1){
            this.imageIndex++
        } else {
            this.imageIndex = 0
        }
        
    },
    previousImage(){
        var lengt = this.images.length
        if(this.imageIndex != 0){
            this.imageIndex--
        } else {
            this.imageIndex = lengt - 1
        }

    }
   }
}

</script>