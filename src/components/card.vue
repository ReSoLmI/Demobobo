<template>
  <div>
    <div class="center">
      001&nbsp;&nbsp;张伟&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      <span @click="closePatient">X</span>
    </div>
    <div class="nav">
      <span>患者待办</span>
      <!-- <span>患者病历</span>
      <span>体征管理</span>
      <span>医嘱管理</span>-->
      <!-- <select
        class="split-input-select"
        style="width:100px;height:26px;margin-left:20px;border:none;background:orange;border-right:1px solid #000;"
      >
        <option value="volvo">患者待办</option>
      </select>-->
      <select
        class="split-input-select"
        style="width:100px;height:26px;margin-left:20px;border:none;background:orange;border-right:1px solid #000;"
      >
        <option value="volvo">电子病历</option>
        <option value="saab">入院评估单</option>
        <option value="saab">每日评估单</option>
        <option value="saab">护理计划</option>
        <option value="saab">护理评价</option>
        <option value="saab">护理记录</option>
      </select>
      <select
        class="split-input-select"
        style="width:100px;height:26px;margin-left:20px;border:none;background:orange;border-right:1px solid #000;"
      >
        <option value="volvo">体征管理</option>
        <option value="saab">体征录入</option>
        <option value="saab">体温单</option>
        <option value="saab">趋势图</option>
      </select>
      <select
        class="split-input-select"
        style="width:100px;height:26px;margin-left:20px;border:none;background:orange;border-right:1px solid #000;"
      >
        <option value="volvo">医嘱管理</option>
        <option value="saab">医嘱查询</option>
        <option value="saab">医嘱执行明细</option>
      </select>
    </div>
    <div class="fast">
      <div>快捷键：</div>
      <ul>
        <li @click="patientdetailShow">&nbsp;&nbsp;&nbsp;&nbsp;患者待办</li>
        <li @click="assesmentShow">入院评估单</li>
        <li @click="dayassesmentShow">每日评估单</li>
        <li @click="nursingplanShow">护理计划</li>
        <li @click="nursingrecordShow">护理记录单</li>
        <li @click="temperaturechartShow">体温单</li>
        <li @click="signinputShow">体征录入</li>
        <li @click="docadviceinquiryShow">医嘱查询</li>
        <li @click="docadviceinquirydetailShow">医嘱执行明细</li>
      </ul>
    </div>
    <div class="main">
      <!-- <div class="main-boot" @closeTemPage="jumpPage()"></div> -->
      <el-tabs v-model="editableTabsValue2" type="card" closable @tab-remove="removeTab">
        <el-tab-pane label="患者待办" name="patientdetail" v-if="flagPatientdetail">
          <patientdetail></patientdetail>
        </el-tab-pane>
        <el-tab-pane label="入院评估单" name="assesment" v-if="flagAssesment">
          <assesment></assesment>
        </el-tab-pane>
        <el-tab-pane label="每日评估单" name="dayassesment" v-if="flagDayassesment">
          <dayassesment></dayassesment>
        </el-tab-pane>
        <el-tab-pane label="护理计划" name="nursingplan" v-if="flagNursingplan">
          <nursingplan></nursingplan>
        </el-tab-pane>
        <el-tab-pane label="护理记录单" name="nursingrecord" v-if="flagNursingrecord">
          <nursingrecord></nursingrecord>
        </el-tab-pane>
        <el-tab-pane label="体温单" name="temperaturechart" v-if="flagTemperaturechart">
          <temperaturechart v-on:show-temevent="showtemevent"></temperaturechart>
        </el-tab-pane>
        <el-tab-pane label="体征录入" name="signinput" v-if="flagSigninput">
          <signinput></signinput>
        </el-tab-pane>
        <el-tab-pane label="医嘱查询" name="docadviceinquiry" v-if="flagDocadviceinquiry">
          <docadviceinquiry v-on:show-docevent="showevent"></docadviceinquiry>
        </el-tab-pane>
        <el-tab-pane label="医嘱查询明细" name="docadviceinquirydetail" v-if="flagDocadviceinquirydetail">
          <docadviceinquirydetail></docadviceinquirydetail>
        </el-tab-pane>
      </el-tabs>

      <!-- <el-tabs v-model="editableTabsValue2" type="card" closable @tab-remove="removeTab">
        <el-tab-pane
          v-for="(item, index) in editableTabs2"
          :key="item.name"
          :label="item.title"
          :name="item.name"
        >{{item.content}}</el-tab-pane>
      </el-tabs>-->
    </div>
  </div>
</template>

<script type="text/javascript">
import assesment from "./assesment.vue";
import dayassesment from "./dayassesment.vue";
import temperaturechart from "./temperaturechart.vue";
import signinput from "./signinput.vue";
import patientdetail from "./patientdetail.vue";
import nursingplan from "./nursingplan.vue";
import nursingrecord from "./nursingrecord.vue";
import docadviceinquiry from "./docadviceinquiry.vue";
import docadviceinquirydetail from "./docadviceinquirydetail.vue";
// import axios from "src/new/libs/axios.js";
export default {
  components: {
    assesment,
    dayassesment,
    temperaturechart,
    signinput,
    patientdetail,
    nursingplan,
    nursingrecord,
    docadviceinquiry,
    docadviceinquirydetail
  },
  data() {
    return {
      // tabIndex: 2,
      editableTabsValue2: "patientdetail", //tab的active
      assesment: {}, //入院评估Obj
      dayassesment: {},
      // temperaturechart: {}, //体温单Obj
      patientdetail: {}, //患者详情Obj
      flagPatientdetail: true,
      flagTemperaturechart: true,
      flagAssesment: true,
      flagDayassesment: true,
      flagNursingplan: false,
      flagNursingrecord: false,
      flagSigninput: true,
      flagDocadviceinquiry: true,
      flagDocadviceinquirydetail: true,
      editableTabs2: [
        {
          title: "Tab 1",
          name: "assesment",
          content: <assesment />
        },
        {
          title: "Tab 2",
          name: "dayassesment",
          content: <dayassesment />
        },
        {
          title: "Tab 3",
          name: "temperaturechart",
          content: <temperaturechart />
        },
        {
          title: "Tab 4",
          name: "signinput",
          content: <signinput />
        },
        {
          title: "Tab 5",
          name: "patientdetail",
          content: <patientdetail />
        },
        {
          title: "Tab 6",
          name: "docadviceinquiry",
          content: <docadviceinquiry />
        },
        {
          title: "Tab 7",
          name: "docadviceinquirydetail",
          content: <docadviceinquirydetail />
        }
      ]
    };
  },
  mounted() {},
  methods: {
    patientdetailShow() {
      this.flagPatientdetail = true;
    },
    assesmentShow() {
      this.flagAssesment = true;
    },
    dayassesmentShow() {
      this.flagDayassesment = true;
    },
    nursingplanShow() {
      this.flagNursingplan = true;
    },
    nursingrecordShow() {
      this.flagNursingrecord = true;
    },
    temperaturechartShow() {
      this.flagTemperaturechart = true;
    },
    signinputShow() {
      this.flagSigninput = true;
    },
    docadviceinquiryShow() {
      this.flagDocadviceinquiry = true;
    },
    docadviceinquirydetailShow() {
      this.flagDocadviceinquirydetail = true;
    },

    closePatient() {},
    removeTab(targetName) {
      let tabs = this.editableTabs2;
      let activeName = this.editableTabsValue2;
      if (activeName === targetName) {
        tabs.forEach((tab, index) => {
          if (tab.name === targetName) {
            let nextTab = tabs[index + 1] || tabs[index - 1];
            if (nextTab) {
              activeName = nextTab.name;
            }
          }
        });
      }

      this.editableTabsValue2 = activeName;
      this.editableTabs2 = tabs.filter(tab => tab.name !== targetName);
    },
    showevent() {
      console.log(999999);
      this.editableTabsValue2 = "docadviceinquirydetail";
      // this.flagDocadviceinquiry = false;
      // this.flagDocadviceinquirydetail = true;
    },
    showtemevent() {
      console.log(77777);
      this.editableTabsValue2 = "signinput";
      // this.flagDocadviceinquiry = false;
      // this.flagDocadviceinquirydetail = true;
    }
    // jumpPage() {
    //   this.flagTemperaturechart = false;
    //   console.log(this.flagTemperaturechart);
    //   this.flagSigninput = true;
    // }
    // showcard() {
    //   console.log(1234);
    //   this.flagDocadviceinquiry = false;
    //   this.flagDocadviceinquirydetail = true;
    // }      @showevent="showcard"
  }
};
</script>



<style type="text/css" lang="scss" scoped>
* {
  padding: 0;
  margin: 0;
}
.center {
  position: absolute;
  top: -40px;
  left: 148px;
  z-index: 1000000;
  padding: 5px 10px;
  line-height: 28px;
  width: 122px;
  border: 1px solid #fff;
  background: #fff;
  color: #666;
  font-size: 14px;
}
.nav {
  height: 28px;
  width: 100%;
  background: orange;
  margin-top: -9px;
  padding-left: 66px;
  span {
    width: 70px;
    height: 20px;
    line-height: 20px;
    float: left;
    font-size: 14px;
    margin-top: 4px;
    padding-left: 15px;
    padding-right: 15px;
    border-right: 1px solid;
  }
}
.main {
  margin-top: 8px;
  .main-boot {
    width: 100px;
    height: 40px;
    // background: #0f0;
    border-bottom: 1px solid #eec;
    float: left;
    margin-left: -100px;
  }
  margin-left: 80px;
}
.fast {
  height: 28px;
  line-height: 28px;
  background: #eec;
  margin-top: 2px;
  div {
    position: absolute;
    display: inline-block;
    font-size: 14px;
    font-weight: bold;
    margin-left: 15px;
    left: 66px;
  }
  ul {
    padding-left: 125px;

    display: inline-block;
    li {
      float: left;
      font-size: 12px;
      padding-left: 20px;
      padding-right: 20px;
    }
  }
}
</style>
