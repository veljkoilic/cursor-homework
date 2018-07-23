
<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-md-6 offset-md-3">
          <MouseMove />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MouseMove from './components/MouseMove.vue'

export default {
  name: 'app',
  components: {
    MouseMove
  }
}
</script>

<style>

</style>