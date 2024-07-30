<script setup>
import Portrait from "./Portrait.vue";
import AboutInfo from "./AboutInfo.vue";
</script>
<template>
    <div
        id="about"
        class="h-full bg-night flex flex-col lg:flex-row justify-between lg:px-32 py-36"
    >
        <Portrait />
        <AboutInfo />
    </div>
</template>
