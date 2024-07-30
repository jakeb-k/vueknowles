<script setup></script>
<template>
    <div
        ref="container"
        class="ml-12 flex-1 bg-night rounded text-[#2db2ff] shadow-about border-[2px] border-neon p-8 relative"
    >
        <h1
            class="absolute -top-7 lg:-top-12 text-2xl lg:text-4xl font-bebas tracking-wider"
        >
            About: <span class="text-white"> Jakeb Knowles</span>
        </h1>

        <h2
            class="type-wrap text-2xl lg:text-3xl font-bebas tracking-wider mb-4"
        >
            <span  v-html="formattedText"></span>
            <span :class="isComplete ? 'opacity-0' : 'cursor'">|</span>
            <i
                v-if="isComplete"
                class="fa-solid fa-wand-magic-sparkles text-white"
            ></i>
        </h2>
    </div>
</template>

<script>
export default {
    data() {
        return {
            typedText: "",
            fullText: `From 'Hello World' to Full-Stack Wizard`,
            typingSpeed: 60, // milliseconds
            isComplete: false,
            whiteWords: ["'Hello World'", "Full-Stack Wizard"],
        };
    },
    mounted() {
        this.createObserver();
    },
    computed: {
        formattedText() {
            let text = this.typedText;
            this.whiteWords.forEach((word) => {
                const regex = new RegExp(word, "g");
                text = text.replace(
                    regex,
                    `<span style="color: white;">${word}</span>`
                );
            });
            return text;
        },
    },
    methods: {
        createObserver() {
            const observer = new IntersectionObserver((entries, observer) => {
                entries.forEach((entry) => {
                    if (entry.isIntersecting) {
                        this.typeText();
                        observer.unobserve(entry.target); // Stop observing once it's in view
                    }
                });
            });

            observer.observe(this.$refs.container);
        },
        typeText() {
            let i = 0;
            const timer = setInterval(() => {
                if (i < this.fullText.length) {
                    this.typedText += this.fullText.charAt(i);
                    i++;
                } else {
                    clearInterval(timer);
                    this.isComplete = true;
                }
            }, this.typingSpeed);
        },
    },
    watch: {
        isComplete() {
            console.log(this.isComplete);
        },
    },
};
</script>
