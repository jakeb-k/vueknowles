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
            <span v-html="formattedText"></span>
            <span :class="isComplete ? 'opacity-0' : 'cursor'">|</span>
            <i
                v-if="isComplete"
                class="fa-solid fa-wand-magic-sparkles text-white"
            ></i>
        </h2>
        <ul class="list-disc font-mono text-neon my-4 lg:mx-6 space-y-6">
            <li>
                <b class="text-lg">Tech Savvy and Versatile:</b> With a
                <span class="text-white"
                    >Bachelors Degree in Information Technology</span
                >
                and
                <span class="text-white"
                    >2 years of real world experience,</span
                >
                I've mastered
                <span class="text-white"
                    >JavaScript, Angular, React, Vue, Laravel, PHP, Python,
                    CSS</span
                >
                and various
                <span class="text-white">database technologies</span>, ready to
                tackle anything from front-end flair to back-end magic.
            </li>
            <li>
                <b class="text-lg">Project Innovator:</b> Projects like
                <a
                    href="public/projects/Aussie_PicklePro"
                    class="text-white hover:underline"
                    >Aussie PicklePro</a
                >
                and <a
                    href="public/projects/Nomster"
                    class="text-white hover:underline"
                    >Nomster</a> aren't just lines on my resume; they're proof of my
                passion for <span class="text-white"
                >creating cool, cutting-edge stuff.</span> I love diving
                into new frameworks and <span class="text-white"
                >turning ideas into reality. </span>
            </li>
            <li>
                <b class="text-lg">Team Player and Adaptable: </b>Whether <span class="text-white"
                >leading a team or
                rolling with the punches,</span> I thrive on new challenges and love
                <span class="text-white"
                    >driving innovation.</span> I'm all about keeping things dynamic and
                <span class="text-white"
                    >making tech magic happen!</span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    data() {
        return {
            typedText: "",
            fullText: `From 'Hello World' to Full-Stack Wizard`,
            typingSpeed: 40, // milliseconds
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
