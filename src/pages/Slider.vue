<template>
    <h1 class="display-3 text-center mb-2">Slider Carousel</h1>

    <div
        class="w-100 position-relative"
        v-for="(color, index) in colors"
        :key="color">
        <transition name="fade">
            <div
                class="w-100 position-absolute"
                :class="color"
                style="height: 60vh"
                v-if="currentSlide == index"></div>
        </transition>
    </div>

    <div class="position-absolute w-100" style="height: 60vh">
        <div
            class="position-absolute bottom-0 pb-2 d-flex justify-content-center w-100">
            <div
                style="height: 15px; width: 15px"
                role="button"
                class="rounded-circle bg-light mx-2 shadow-sm"
                :class="{ 'bg-dark': currentSlide == index }"
                v-for="(slider, index) in colors"
                :key="slider"
                @click="setActive(index)"></div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            currentSlide: 0,
            colors: ['bg-primary', 'bg-warning', 'bg-danger'],
            interval: '',
            isShowing: true
        }
    },
    mounted() {
        this.interval = setInterval(() => {
            if (this.currentSlide === 2) {
                this.currentSlide = 0
            } else {
                this.currentSlide++
            }
        }, 3000)
    },
    unmounted() {
        clearInterval(this.interval)
    },
    methods: {
        setActive(index) {
            this.currentSlide = index
        }
    }
}
</script>

<style>
body {
    margin: 0;
}
.fade-enter-active,
.fade-leave-active {
    transition: all 0.7s ease;
}

.fade-enter-from {
    opacity: 0;
    transform: translateX(-100%);
}
.fade-leave-to {
    opacity: 0;
    transform: translateX(100%);
}
</style>
