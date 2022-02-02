<template>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container">
            <router-link class="navbar-brand" to="/">Vue3</router-link>
            <button
                class="navbar-toggler"
                type="button"
                data-bs-toggle="collapse"
                data-bs-target="#navbarNav"
                aria-controls="navbarNav"
                aria-expanded="false"
                aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item" v-for="item in list" :key="item.to">
                        <router-link
                            class="nav-link active"
                            aria-current="page"
                            :to="item.to">
                            {{ item.title }}
                        </router-link>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script>
export default {
    data() {
        return {
            list: [
                { title: 'DC Heros List', to: '/dc-heros' },
                { title: 'Calendar', to: '/calendar' },
                { title: 'Markdown', to: '/markdown' }
            ]
        }
    }
}
</script>

<style></style>
