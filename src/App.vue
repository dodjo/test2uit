<template>
  <div id="app" class="wrapper">
    <catalog></catalog>
  </div>
</template>

<script>
import Catalog from './components/Catalog.vue'
import '@/assets/scss/base.scss';

export default {
  name: 'app',
  components: {
    Catalog
  }
}
</script>

