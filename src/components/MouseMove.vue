<template>
  <div v-on:mousemove="sendCursorLocation" class="container">
      <img src="https://goo.gl/uRQJKR" alt="" class="cursor" v-bind:style="{ left: x + 'px', top: y + 'px' }">
  </div>
</template>

<script>
import io from 'socket.io-client';
export default {
    data() {
        return {
            y: '',
            x: '',
            socket : io('localhost:3001')
        }
    },
    methods: {
        sendCursorLocation(e) {
            this.socket.emit('sendLocation', {
                x: e.pageX, y: e.pageY
            });
        },
    },
    mounted() {
       this.socket.on('allMouseActivity', (data) => {
            console.log(data.coords);
            this.x = data.coords.x;
            this.y = data.coords.y;
        });
    },
}
</script>

<style>
.cursor {
    width: 20px;
    position: absolute;
}
.container {
    width: 100vw;
    height: 100vh;
}
</style>