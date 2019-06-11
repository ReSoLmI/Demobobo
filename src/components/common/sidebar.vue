<template>
  <!-- <transition name="bounce"> -->
  <aside class="aside">
    <!--       <ul>

        <li><a href="#/home">home</a></li>
        <li><a href="#/film">film</a></li>
        <li><a href="#/card">card</a></li>
    </ul>-->

    <!-- hash -->

    <ul @click="handleClick()">
      <!-- 声明式导航 -->
      <router-link to="/home" tag="li" activeClass="kerwinactive">床位</router-link>
      <router-link to="/card" tag="li" activeClass="kerwinactive">患者</router-link>
      <router-link to="/film" tag="li" activeClass="kerwinactive">病区</router-link>
      <router-link to="/cish" tag="li" activeClass="kerwinactive">管理</router-link>
      <router-link to="/bish" tag="li" activeClass="kerwinactive">统计</router-link>
      <router-link to="/bish" tag="li" activeClass="kerwinactive">提醒</router-link>
    </ul>
  </aside>
  <!-- </transition> -->
</template>

<script type="text/javascript">
export default {
  props: ["show"],
  methods: {
    handleClick() {
      this.$emit("kerwinevent"); //触发kerwinevent;
      // 床号、患者、病区、管理、统计、提醒
    }
  }
};
</script>



<style type="text/css" lang="scss" scoped>
aside {
  position: fixed;
  margin-top: 0px;
  width: 5%;
  height: 100%;
  top: 40px;
  left: 0px;
  // background: #eee;
  color: #000;
  z-index: 100;
  text-align: center;
  li {
    padding: 9px;
    border-bottom: 1px solid #ccc;
    border-right: 1px solid #ccc;
    width: 32px;
    height: 78px !important;
    line-height: 78px;
    background: #eee;
  }
  .kerwinactive {
    background: rgb(255, 204, 102);
  }
}

// .bounce-enter-active {
//   animation: bounce-in 0.5s;
// }
// .bounce-leave-active {
//   animation: bounce-in 0.5s reverse;
// }
// @keyframes bounce-in {
//   0% {
//     transform: translateX(-100%);
//     opacity: 0;
//   }
//   100% {
//     transform: translateX(0px);
//     opacity: 1;
//   }
// }
</style>
