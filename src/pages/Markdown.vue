<template>
    <h1 class="display-3 text-center mb-2">Markdown</h1>
    <section class="row">
        <article class="col" style="height: 75vh">
            <textarea
                class="w-100 h-100 form-control"
                :value="text"
                @input="updated"></textarea>
        </article>

        <article
            class="col bg-light"
            style="height: 75vh"
            v-html="markedText"></article>
    </section>
</template>

<script>
import { marked } from 'marked'

export default {
    data() {
        return {
            text: '',
            timeOut: ''
        }
    },
    computed: {
        markedText() {
            return marked(this.text)
        }
    },
    methods: {
        updated(e) {
            const task = () => (this.text = e.target.value)

            this.debounce(task, 500)
        },
        debounce(func, wait = 1000) {
            clearTimeout(this.timeOut)

            this.timeOut = setTimeout(func, wait)
        }
    }
}
</script>

<style></style>
