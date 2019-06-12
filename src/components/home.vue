<template>
  <div v-if="simple">
    <ul>
      <li class="chut">我的患者&nbsp;4</li>
      <li class="hubt">全部患者&nbsp;26</li>
      <li class="style-right">护理等级 v</li>
      <li class="style-right">新病人2</li>
      <li class="style-right">高危压疮3</li>
      <li class="style-right">高危跌倒3</li>
      <li class="style-right">约束具3</li>
      <li class="style-right">导管2 v</li>
      <li class="style-right">新医嘱3</li>
      <li class="style-right">体温异常2</li>
    </ul>

    <div style="width:1334px;">
      <img src="../../static/image/C1.png" alt class="fl-r" @click="changemode">

      <img src="../../static/image/12121/001.jpg" alt class="img1" @click="changemodetocard">

      <img src="../../static/image/12121/002.jpg" alt class="img2" @click="changemodetocard">

      <img src="../../static/image/12121/003.jpg" alt class="img3" @click="changemodetocard">

      <img src="../../static/image/12121/004.jpg" alt class="img4" @click="changemodetocard">

      <img src="../../static/image/12121/005.jpg" alt class="img1" @click="changemodetocard">

      <img src="../../static/image/12121/006.jpg" alt class="img6" @click="changemodetocard">

      <img src="../../static/image/12121/007.jpg" alt class="img7" @click="changemodetocard">

      <img src="../../static/image/12121/008.jpg" alt class="img8" @click="changemodetocard">

      <img src="../../static/image/12121/009.jpg" alt class="img1" @click="changemodetocard">

      <img src="../../static/image/12121/010.jpg" alt class="img9" @click="changemodetocard">

      <img src="../../static/image/12121/011.jpg" alt class="img10" @click="changemodetocard">

      <img src="../../static/image/12121/012.jpg" alt class="img11" @click="changemodetocard">

      <img src="../../static/image/12121/013.jpg" alt class="img1" @click="changemodetocard">

      <img src="../../static/image/12121/014.jpg" alt class="img12" @click="changemodetocard">

      <img src="../../static/image/12121/015.jpg" alt class="img13" @click="changemodetocard">

      <img src="../../static/image/12121/016.jpg" alt class="img14" @click="changemodetocard">
    </div>
  </div>

  <div v-else>
    <ul>
      <li class="chut">我的患者&nbsp;4</li>
      <li class="hubt">全部患者&nbsp;26</li>
      <li class="style-right">护理等级 v</li>
      <li class="style-right">新病人2</li>
      <li class="style-right">高危压疮3</li>
      <li class="style-right">高危跌倒3</li>
      <li class="style-right">约束具3</li>
      <li class="style-right">导管2 v</li>
      <li class="style-right">新医嘱3</li>
      <li class="style-right">体温异常2</li>
    </ul>
    <img src="../../static/image/C1.png" alt class="fl-r" @click="changemode">
    <div @click="changemodetocard">
      <el-table
        :data="tableData3"
        height="530"
        class="table"
        :header-cell-style="{
        'text-align':'center',
        'color':'#000',
        'font-size':'12px',
        'font-weight':'300',
        'background':'#eee'
        }"
      >
        <el-table-column prop="number" label="床号↓" width="60"></el-table-column>
        <el-table-column prop="name" label="姓名" width="60"></el-table-column>
        <el-table-column prop="sex" label="性别" width="50"></el-table-column>
        <el-table-column prop="age" label="年龄" width="50"></el-table-column>
        <el-table-column prop="mrn" label="MRN" width="60"></el-table-column>
        <el-table-column prop="history" label="过敏史" width="80"></el-table-column>
        <el-table-column prop="time" label="入院时间" width="80"></el-table-column>
        <el-table-column prop="doctor" label="主治医生" width="80"></el-table-column>
        <el-table-column prop="level" label="护理级别" width="80"></el-table-column>
        <el-table-column prop="diagnose" label="诊断" width="180"></el-table-column>
        <el-table-column prop="food" label="饮食" width="180"></el-table-column>
        <el-table-column prop="insurance" label="医保费别" width="80"></el-table-column>
        <el-table-column prop="fees" label="预缴款项" width="80"></el-table-column>
        <el-table-column prop="total" label="费用合计" width="100"></el-table-column>
        <el-table-column prop="tel" label="联系电话" width="100"></el-table-column>
      </el-table>
    </div>
  </div>
</template>

<script type="text/javascript">
// require('vue-swipe/dist/vue-swipe.css');//vue-swipe css 引入

import "vue-swipe/dist/vue-swipe.css";
import { Swipe, SwipeItem } from "vue-swipe";

import { Indicator } from "mint-ui";

import axios from "axios"; //
export default {
  data() {
    return {
      simple: true,
      list: [],
      looplist: [
        {
          number: "001",
          name: "张伟",
          encode: "9812345",
          sex: "男",
          age: "69岁",
          level: "1",
          state: [
            {
              logo: ["新", "疮", "跌", "束", "管", "脱落"]
            }
          ]
        },
        {
          number: "002",
          name: "王伟",
          encode: "9812345",
          sex: "男",
          age: "60岁",
          level: "1",
          state: [
            {
              logo: ["疮", "管"]
            }
          ]
        },
        {
          number: "003",
          name: "王芳",
          encode: "9812345",
          sex: "女",
          age: "18岁",
          level: "1",
          state: [
            {
              logo: ["跌", "束", "管", "脱落"]
            }
          ]
        },
        {
          number: "004",
          name: "李伟",
          encode: "9812345",
          sex: "男",
          age: "90岁",
          level: "1",
          state: [
            {
              logo: ["脱落"]
            }
          ]
        },
        {
          number: "005",
          name: "王秀英",
          encode: "9812345",
          sex: "女",
          age: "5岁",
          level: "1",
          state: [
            {
              logo: ["新", "疮", "跌", "束", "管", "脱落"]
            }
          ]
        }
      ],
      tableData3: [
        {
          number: "001",
          name: "张伟",
          sex: "男",
          age: "60岁",
          mrn: "90821234",
          history: "头孢",
          time: "06-1",
          doctor: "李医生",
          level: "二级",
          diagnose: "累及循环和呼吸系统特指症状和体征。",
          food: "清淡为主",
          insurance: "医保病人",
          fees: "8000",
          total: "6634.23",
          tel: "176-1208-1520"
        },
        {
          number: "002",
          name: "王伟",
          sex: "男",
          age: "50岁",
          mrn: "87651234",
          history: "青霉素",
          time: "06-26",
          doctor: "赵医生",
          level: "三级",
          diagnose: "特指症状和体征。",
          food: "清淡为主，忌辛辣、生冷",
          insurance: "医保病人",
          fees: "1000",
          total: "534.23",
          tel: "188-6008-1000"
        },
        {
          number: "003",
          name: "王芳",
          sex: "女",
          age: "18岁",
          mrn: "12345678",
          history: "头孢",
          time: "04-15",
          doctor: "陈医生",
          level: "一级",
          diagnose: "系统特指症状和体征。",
          food: "清淡为主，忌辛辣、生冷",
          insurance: "医保病人",
          fees: "9000",
          total: "9534.23",
          tel: "180-6888-1990"
        },
        {
          number: "004",
          name: "李伟",
          sex: "男",
          age: "69岁",
          mrn: "90049362",
          history: "青霉素",
          time: "06-10",
          doctor: "王医生",
          level: "一级",
          diagnose: "累及循环和呼吸系统特指症状和体征。",
          food: "清淡为主，忌辛辣、生冷",
          insurance: "医保病人",
          fees: "3000",
          total: "2534.23",
          tel: "186-6808-1520"
        },
        {
          number: "005",
          name: "王秀英",
          sex: "男",
          age: "69岁",
          mrn: "90049362",
          history: "青霉素",
          time: "06-10",
          doctor: "王医生",
          level: "一级",
          diagnose: "累及循环和指症状和体征。",
          food: "清淡为主，忌辛辣、生冷",
          insurance: "医保病人",
          fees: "3000",
          total: "2534.23",
          tel: "186-6808-1520"
        },
        {
          number: "006",
          name: "李娜",
          sex: "男",
          age: "69岁",
          mrn: "90049362",
          history: "青霉素",
          time: "06-10",
          doctor: "王医生",
          level: "一级",
          diagnose: "累及循环和呼吸系统特指症状和体征。",
          food: "清淡为主，忌辛辣、生冷",
          insurance: "医保病人",
          fees: "3000",
          total: "2534.23",
          tel: "186-6808-1520"
        },
        {
          number: "007",
          name: "张秀英",
          sex: "女",
          age: "10岁",
          mrn: "90049362",
          history: "青霉素",
          time: "06-10",
          doctor: "王医生",
          level: "一级",
          diagnose: "累及循环和呼吸系统特指症状和体征。",
          food: "清淡为主，忌辛辣、生冷",
          insurance: "医保病人",
          fees: "3000",
          total: "2534.23",
          tel: "186-6808-1520"
        },
        {
          number: "08",
          name: "刘伟",
          sex: "男",
          age: "99岁",
          mrn: "90044462",
          history: "青霉素",
          time: "06-10",
          doctor: "任医生",
          level: "四级",
          diagnose: "累及循环和呼吸系统特指症状和体征。",
          food: "清淡为主，忌辛辣、生冷",
          insurance: "医保病人",
          fees: "3000",
          total: "2534.23",
          tel: "186-6808-1520"
        }
      ]
    };
  },

  components: {
    swipe: Swipe,
    "swipe-item": SwipeItem //注册局部组件
  },

  mounted() {
    this.$store.commit("myChangeTitle", "");
  },
  methods: {
    changemode() {
      console.log(123);
      this.simple = !this.simple;
    },
    changemodetocard() {
      this.$router.push({
        path: "/card/"
      });
    }
  }
};
</script>



<style type="text/css" lang="scss" scoped>
ul {
  float: left;
  display: flex;
  margin-left: 50px;
  li {
    width: 100px;
    text-align: center;
    height: 40px;
    line-height: 40px;
    border: 1px solid #eee;
    font-size: 14px;
    margin-top: -10px;
  }
}
img {
  display: inline-block;
  margin-left: 25px;
  margin-top: 25px;
}
.img1 {
  margin-left: 75px;
}
// .img2 {
//   padding-bottom: 4px;
// }
// .img3 {
//   padding-bottom: 5px;
// }
.img5 {
  padding-bottom: -2px;
}
.img6 {
  padding-left: 3px;
}
// .img8 {
//   padding-bottom: 6px;
// }
.img9 {
  padding-left: 3px;
}
// .img10 {
//   padding-left: 4px;
// }
// .img11 {
//   padding-left: 11px;
// }
.img12 {
  padding-left: 3px;
}
// .img13 {
//   padding-left: 4px;
// }
.img14 {
  padding-left: 6px;
}
// .img15 {
//   padding-left: 7px;
// }
.chut {
  background: #eee;
}
.hubt {
  color: rgb(55, 55, 243);
}
.style-right {
  color: #bbb;
}
.fl-r {
  float: right;
  // display: inline-block;

  text-align: center;
  // height: 40px;
  line-height: 40px;
  font-size: 14px;
  margin-top: -10px;
}
</style>
