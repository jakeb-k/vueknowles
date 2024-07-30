<script setup>
import { ref, onMounted, defineProps } from 'vue'; 
import TechBox from '@/Components/Detail/TechBox.vue'; 
import ProjectInfo from '@/Components/Detail/ProjectInfo.vue'; 
import MobileView from '@/Components/Detail/MobileView.vue'; 
import DesktopView from '@/Components/Detail/DesktopView.vue'; 

const props = defineProps({
    project: Object,
    projectName: String,
    techs: {
        type: Array,
        default: () => ([]), // provide a default empty array
    },
    desc: Array,
    viewMode: String, 
    itemCount: Number,
})
const typedText = ref('');
const projectName = ref(props.projectName);
const typingSpeed = 100; // milliseconds
var viewMode = ref(props.viewMode); 
const isMobile = props.viewMode == 'mobile' ? true : false; 
function typeText() {
  let i = 0;
  const timer = setInterval(() => {
    if (i < projectName.value.length) {
      typedText.value += projectName.value.charAt(i);
      i++;
    } else {
      clearInterval(timer);
    }
  }, typingSpeed);
}

onMounted(() => {
  typeText();
});

function viewSwitch(){
    if(props.viewMode == 'web' && props.projectName != 'F-Service') {
        viewMode.value = viewMode.value === 'web' ? 'mobile' : 'web';
    }
}
</script>
<template>
    <div class="h-fit w-full bg-smoke">

        <div class="pt-36 ml-[5%] bg-smoke">
            <h1 class="type-wrap text-5xl text-night font-bebas tracking-wider ">
                <span>{{ typedText }}</span> 
                <span class="cursor">|</span>
            </h1>
            <div class=" w-full lg:w-fit flex flex-row flex-wrap items-center">
                <div v-for="tech in techs">
                    <TechBox :tech="tech"></TechBox>
                </div>
                <button v-if="!isMobile" @click="viewSwitch()" class="ml-2">
                    <i class="fa-solid h-full text-5xl hover:text-ocean duration-150 ease-in-out"
                    :class="viewMode == 'web' ?' fa-mobile-screen' : 'fa-desktop'"></i>
                </button>
            </div>
        </div>

        <div class="flex flex-row w-11/12 mx-auto h-fit relative lg:py-14"
        :class="viewMode == 'web' ?' 2xl:py-32' : '2xl:pt-32'">
             <ProjectInfo class="mr-10 flex-1" :desc="desc" :url="props.project.url"></ProjectInfo>
             <div class="flex-1">
                <DesktopView v-if="viewMode == 'web'" :name="props.project.name" :itemCount="itemCount"></DesktopView>
                <MobileView v-if="viewMode == 'mobile'" :name="props.project.name" :itemCount="itemCount"></MobileView>
             </div>

             
         </div>
        
        
    </div>
</template>
