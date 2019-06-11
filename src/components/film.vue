<template>
  <div>
    <div class="nav">
      <span style="width: 86px;">体征批量录入</span>
      <span>医嘱管理</span>
      <span>代办提醒</span>
      <span>统计分析</span>
    </div>
    <!-- <div class="fast">
      <div>快捷键：</div>
      <ul>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;患者代办</li>
        <li>入院评估单</li>
        <li>每日评估单</li>
        <li>护理计划</li>
        <li>护理记录单</li>
        <li>体温单</li>
        <li>体征录入</li>
        <li>医嘱查询</li>
        <li>医嘱执行明细</li>
      </ul>
    </div>-->
    <div class="main">
      <div class="main-boot"></div>
      <el-tabs v-model="activeName" type="card" closable @tab-remove="removeTab">
        <el-tab-pane label="待办事项" name="todoitems" v-if="flagTodoitems">
          <todoitems></todoitems>
        </el-tab-pane>
        <el-tab-pane label="体征批量录入" name="signbatchinput" v-if="flagSignbatchinput">
          <signbatchinput></signbatchinput>
        </el-tab-pane>
        <el-tab-pane label="医嘱拆分" name="docacvicesplit" v-if="flagDocacvicesplit">
          <docacvicesplit></docacvicesplit>
        </el-tab-pane>
        <el-tab-pane label="医嘱巡视" name="docadvicepatrol" v-if="flagDocadvicepatrol">
          <docadvicepatrol></docadvicepatrol>
        </el-tab-pane>
      </el-tabs>
    </div>
  </div>
</template>

<script type="text/javascript">
import todoitems from "./todoitems.vue";
import signbatchinput from "./signbatchinput.vue";
import docacvicesplit from "./docacvicesplit.vue";
import docadvicepatrol from "./docadvicepatrol.vue";
// import axios from "src/new/libs/axios.js";
export default {
  components: {
    todoitems,
    signbatchinput,
    docacvicesplit,
    docadvicepatrol
  },
  data() {
    return {
      activeName: "signbatchinput", //tab的active
      assesment: {}, //入院评估Obj
      dayassesment: {},
      // temperaturechart: {}, //体温单Obj
      patientdetail: {}, //患者详情Obj
      flagTodoitems: true,
      flagSignbatchinput: true,
      flagDocacvicesplit: true,
      flagDocadvicepatrol: true,
      flagPatientdetail: true,
      flagTemperaturechart: true,
      flagAssesment: true,
      flagDayassesment: true,
      flagNursingplan: true,
      flagNursingrecord: true,
      flagSigninput: true,
      flagDocadviceinquiry: true
    };
  },
  methods: {
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
    }
  }
};
</script>



<style type="text/css" lang="scss" scoped>
* {
  padding: 0;
  margin: 0;
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
