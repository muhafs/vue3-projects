<template>
    <div class="row justify-content-center">
        <div class="col-6">
            <h1 class="display-3 text-center mb-2">DC Heros</h1>

            <div class="input-group mb-3">
                <input
                    type="text"
                    class="form-control"
                    placeholder="type superhero's name"
                    v-model="newHero"
                    @keyup.enter="addHero" />
                <button class="btn btn-outline-secondary" @click="addHero">
                    Add
                </button>
            </div>

            <ul class="list-group">
                <li
                    class="list-group-item d-flex justify-content-between align-items-center px-5"
                    v-for="(hero, index) in dcHero"
                    :key="hero.name">
                    <div>
                        {{ hero.name }}
                    </div>
                    <button
                        class="btn btn-danger btn-sm px-3"
                        @click="deleteHero(index)">
                        x
                    </button>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newHero: '',
            dcHero: [
                { name: 'Aquaman' },
                { name: 'Batman' },
                { name: 'Superman' },
                { name: 'Flash' },
                { name: 'Wonderwomen' }
            ]
        }
    },
    methods: {
        addHero() {
            if (!this.newHero) {
                return
            }
            this.dcHero.push({ name: this.newHero })
            this.newHero = ''
        },
        deleteHero(id) {
            this.dcHero.splice(id, 1)
        }
    }
}
</script>

<style></style>
