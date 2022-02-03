<template>
    <div class="container">
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
    </div>
</template>

<script>
import { marked } from 'marked'
import debounce from '../utilities/mixins/debounce'

export default {
    mixins: [debounce],
    data() {
        return {
            text: ''
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
        }
    }
}
</script>

<style></style>
