<script setup>
import { onMounted } from "vue";

const props = defineProps({
    desc: Array,
    url: String,
});
</script>
<template>
    <div
        class="bg-night h-fit lg:w-5/12 p-8 rounded-lg border-[2.5px] border-ocean"
    >
        <p class="font-mono text-smoke text-md font-bold 2xl:text-lg">
            {{ desc[0] }}
        </p>
        <ul
            class="list-disc font-mono text-xs ml-4 lg:text-sm text-smoke my-4 lg:mx-6 space-y-4"
        >
            <li>{{ desc[1] }}</li>
            <li>{{ desc[2] }}</li>
            <li>{{ desc[3] }}</li>
        </ul>
        <a :href="url">
            <button
                class="bg-smoke block my-4 mx-auto text-center w-8/12 lg:w-5/12 text-ocean font-bebas tracking-wider text-2xl py-2.5 2xl:py-5 rounded-xl shadow-cta-pre transform hover:translate-x-[12px] hover:translate-y-[12px] hover:shadow-cta-post hover:text-white hover:bg-ocean hover:underline transition duration-200 linear"
            >
                View Project!
            </button>
        </a>
    </div>
</template>
