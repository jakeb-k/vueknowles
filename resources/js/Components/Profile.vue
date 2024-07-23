<template>
    <div class="2xl:h-3/5 h-4/5">
        <img
            src="../assets/images/profile.webp"
            alt="profile"
            class="h-full my-auto border-[3px] border-gray-800 rounded-full object-cover"
        />
    </div>
</template>

<script>
import profileUrl from "../assets/images/profile.webp";

export default {
    data() {
        return {
            profileUrl,
        };
    },
};
</script>
