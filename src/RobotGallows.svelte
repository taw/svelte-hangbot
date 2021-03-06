<script>
  export let stage = 0;
</script>

<div class="gallows">
  <div class="robot stage1" class:hide={stage < 1}>🤖</div>
  <div class="robot stage2" class:hide={stage < 2}></div>
  <div class="robot stage3" class:hide={stage < 3}></div>
  <div class="robot stage4" class:hide={stage < 4}></div>
  <div class="robot stage5" class:hide={stage < 5}></div>
  <div class="robot stage6" class:hide={stage < 6}></div>
  <div class="robot stage7" class:hide={stage < 7}>🚔</div>
  <div class="robot stage8" class:hide={stage < 8}>🚔</div>
</div>

Hanging of 🤖 at stage {stage} of 8.

<style>
  .gallows {
    display: inline-block;
    margin: auto;
    height: 200px;
    height: 200px;
    position: relative;
  }
  .robot {
    display:  inline-block;
    position: absolute;
    background-color: blue;
    text-align: center;
  }
  .stage1 {
    height: 20px;
    width: 20px;
    top: 0px;
    left: 90px;
  }
  .stage2 {
    height: 80px;
    width: 60px;
    top: 20px;
    left: 70px;
  }
  .stage3 {
    height: 10px;
    width: 40px;
    top: 30px;
    left: 30px;
  }
  .stage4 {
    height: 10px;
    width: 40px;
    top: 30px;
    left: 130px;
  }
  .stage5 {
    height: 40px;
    width: 10px;
    top: 100px;
    left: 80px;
  }
  .stage6 {
    height: 40px;
    width: 10px;
    top: 100px;
    left: 110px;
  }
  .stage7 {
    height: 20px;
    width: 20px;
    top: 140px;
    left: 70px;
  }
  .stage8 {
    height: 20px;
    width: 20px;
    top: 140px;
    left: 110px;
  }
  .robot.hide {
    display: none;
  }
</style>
