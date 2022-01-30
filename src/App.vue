<template>
  <AppHeader />
  <div class="container">
    <DcHeros />
  </div>
</template>

<script>
import AppHeader from '@/components/AppHeader.vue'
import DcHeros from '@/components/DcHeros.vue'

export default {
  components: { AppHeader, DcHeros },
}
</script>

<style></style>
