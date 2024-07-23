<script setup>
import Portrait from "./Portrait.vue";
import AboutInfo from "./AboutInfo.vue";
</script>
<template>
    <div
        id="about"
        class="h-full bg-night flex flex-col lg:flex-row justify-around py-36 px-48"
    >
        <Portrait />
        <AboutInfo />
    </div>
</template>
