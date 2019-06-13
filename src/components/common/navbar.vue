<template>
  <nav>
    <div class="left">
      <slot></slot>
      <span>智慧医疗</span>
    </div>
    <!-- <div class="center" v-show="mode">
      001&nbsp;&nbsp;刘德安&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      <span
        @click="closePatient"
      >X</span>
    </div>-->
    <div class="right">
      <span class="right-time">时间：2019年06月01日 12:29:22</span>
      <span class="right-departments">消化内科&nbsp;∨</span>

      <span class="right-time">张护士&nbsp;∨</span>
    </div>
  </nav>
</template>

<script type="text/javascript">
import { mapState } from "vuex";
export default {
  data() {
    return {};
  },
  computed: {
    // mode: {
    //   // window.location.pathname == "/card";
    //   get() {
    //     return window.location.pathname == "/card" ? true : false;
    //   },
    //   set(val) {
    //     if (val) {
    //       window.location.pathname = "/card";
    //     } else {
    //       window.location.pathname;
    //     }
    //   }
    // }
  },
  mounted() {
    // if (window.location.pathname == "/card") {
    //   this.mode = true;
    // } else {
    //   this.mode = false;
    // }
  },

  methods: {
    closePatient() {
      this.$router.push({
        path: "/home"
      });
      // this.patinetShow = false;
      // console.log(window.location.href);
    }
  }
};
</script>

<style type="text/css" lang="scss" scoped>
nav {
  position: fixed;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 40px;
  background: orange;
  line-height: 40px;
  color: white;
  z-index: 10;
  .left {
    float: left;
    margin-left: 50px;
  }
  // .center {
  //   display: inline-block;
  //   margin-left: 25px;
  //   padding: 5px 10px;
  //   line-height: 28px;
  //   width: 122px;
  //   border: 1px solid #fff;
  //   background: #fff;
  //   color: #666;
  //   font-size: 14px;
  // }

  .right {
    float: right;
  }
  .right-time {
    margin-right: 20px;
  }
  .right-departments {
    margin-right: 40px;
  }
}
</style>
