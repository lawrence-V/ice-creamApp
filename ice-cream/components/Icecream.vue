<template>
  <div>
    <div class="icecream" id="icecream">
      <p class="cone"></p>
      <div
        class="scoop"
        v-for="cartItem in icecream"
        :key="cartItem"
        :class="cartItem.name.toLowerCase()"
      ></div>
      <div class="cherry" v-if="icecream.length > 0"></div>
      <div class="question" v-else></div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  icecream: {
    type: Array,
    required: true,
  },
});

const { icecream } = toRefs(props);
</script>

<style scoped>
.cherry {
  background: url(/cherry.png) center/cover no-repeat;
  width: 50px;
  height: 77px;
  z-index: 3;
  margin-bottom: -10px;
}

.question {
  background: url(/question.png) center/cover no-repeat;
  width: 48px;
  height: 48px;
  z-index: 3;
  margin-bottom: 25px;
}

.icecream {
  display: flex;
  flex-direction: column-reverse;
  justify-content: center;
  align-items: center;
  height: 100%;
  width: 100%;
  min-height: 632px;
}

.cone {
  margin-top: -20px;
  height: 0px;
  width: 0px;
  border-right: 45px solid transparent;
  border-left: 45px solid transparent;
  border-top: 140px solid tan;
  z-index: 1;
}

.scoop {
  width: 100px;
  height: 80px;
  border-radius: 100%;
  position: relative;
  margin-bottom: -45px;
  z-index: 3;
}

.scoop::after {
  content: "";
  position: absolute;
  bottom: 10px;
  left: -10px;
  height: 35px;
  width: 120px;
  border-radius: 100%;
  z-index: 2;
}

div.scoop:first-of-type {
  margin-bottom: 0px;
}

.vanilla,
.vanilla::after {
  background-color: blue;
}

.chocolate,
.chocolate::after {
  background-color: red;
}

.chocolate,
.chocolate::after {
  background: #b98160;
}

.vanilla,
.vanilla::after {
  background: #fae8b6;
}

.strawberry,
.strawberry::after {
  background: pink;
}

.orange,
.orange::after {
  background: orange;
}
</style>