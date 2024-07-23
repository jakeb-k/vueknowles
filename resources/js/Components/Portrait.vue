<template>
    <div class="card-container">
        <div class="card">
            <div
                class="card-front rounded border-2 border-neon cursor-pointer"
            ></div>
            <div
                class="card-back rounded border-2 border-neon shadow-about"
            ></div>
        </div>
    </div>
</template>

<script>
import portraitUrl from "../assets/images/jakey.webp";

export default {
    data() {
        return {
            portraitUrl,
            isFlipped: false,
        };
    },
    mounted() {},
    methods: {},
};
</script>
