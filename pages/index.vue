<template>
  <div class="wrapper">
    <canvas id="game"></canvas>
  </div>
</template>
<script>

export default {
  data(){
    return{
      player: {
        x: 10,
        y: 10,
        xSpeed: 1,
        ySpeed: 1
      },
      speed: 0.1,
      wPressed: false,
      sPressed: false,
      aPressed: false,
      dPressed: true,
      upPressed: false,
      downPressed: false,
      leftPressed: false,
      rightPressed: false,
      SPEED: 1,
    // canvas: this.$refs.canvas,
    // context: this.canvas.getContext(),
     
    }
  },
  computed:{

  },
  mounted(){

    this.animate()
  },
  methods:{
    animate() {
      // if (wPressed) {
      //     player.ySpeed = player.ySpeed - SPEED;
      // }
      // if (sPressed) {
      //     player.ySpeed = player.ySpeed + SPEED;
      // }

      let {wPressed, sPressed, aPressed, dPressed, player, SPEED, canvas, context} = this 
      canvas = document.querySelector('#game');
      context = canvas.getContext('2d');
      if (wPressed) {player.ySpeed = player.ySpeed - SPEED;}
      if (sPressed) {player.ySpeed = player.ySpeed + SPEED;}
      if (aPressed) {player.xSpeed = player.xSpeed - SPEED;}
      if (dPressed) {player.xSpeed = player.xSpeed + SPEED;}

      
      player.x = player.x + player.xSpeed;
      player.y = player.y + player.ySpeed;

      // context.clearRect(0, 0, canvas.width, canvas.height);    
      // context.fillRect(player.x, player.y, 10, 10);
      debugger
      if (player.x > canvas.width) {
          player.xSpeed = -player.xSpeed;
          player.x = canvas.width - 1;
      }
      if (player.y > canvas.height) {
          player.ySpeed = -player.ySpeed;
          player.y = canvas.height - 1;
      }
      if (player.x < 0) {
          player.xSpeed = -player.xSpeed;
          player.x = 1;
      }
      if (player.y < 0) {
          player.ySpeed = -player.ySpeed;
          player.y = 1;
      }

      requestAnimationFrame(() => {
          this.animate();
      });
}
  },

}
</script>
<style scoped>
@import '~/assets/styles/oknoGryStyles.css';
</style>