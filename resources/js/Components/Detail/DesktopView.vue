<script setup>

import { ref } from 'vue'; 

const props = defineProps({
    name: String,
    itemCount: Number,
})
const index = ref(0);
let slideshowInterval = null;


function startSlideshow() {
    slideshowInterval = setInterval(() => {
        if (index.value < props.itemCount - 1) {
            index.value++;
        } else {
            index.value = 0;
        }
    }, 3000);
}

function setIndex(n) {
    index.value = n;
    clearInterval(slideshowInterval);
    startSlideshow();  // Restart the slideshow after setting the index
}

startSlideshow();
</script>

<template>
    <div class="w-full ">
        <div class="h-full relative 2xl:-mt-10"> 
            <img class="border-8 border-night rounded-xl pb-4 bg-night" :src="'/vueknowles/resources/js/assets/images/'+name+'/web/'+index+'.webp'" >
            <div class="w-[5%] mx-auto h-[30px] bg-night"></div>
            <div class="w-11/12 rounded-2xl mx-auto h-[30px] bg-night"></div>

            <div class="flex flex-row absolute bottom-2 items-center w-full justify-center ">
                <button 
                    class="p-2 rounded-full mr-2" 
                    v-for="n in props.itemCount" 
                    :key="n"
                    :class="{ 'bg-blue-500': index === n - 1, 'bg-gray-500': index !== n - 1 }"
                    @click="setIndex(n - 1)">
                </button>
            </div>
                
        </div>
           
    </div>

</template>