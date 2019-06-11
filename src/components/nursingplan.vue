<template>
  <div>
    <el-table ref="table" :data="info" :span-method="colspanMethod">
      <el-table-column type="selection" width="40"></el-table-column>
      <el-table-column label="序号" width="60">
        <template slot-scope="scope">{{scope.$index+1}}</template>
      </el-table-column>
      <el-table-column label="单位" width="260">
        <template slot-scope="scope">{{scope.row.ORGNAME}}</template>
      </el-table-column>
      <el-table-column label="文件名称" width="260">
        <template slot-scope="scope">{{scope.row.jyFile.FILE_NAME}}</template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script type="text/javascript">
import axios from "axios";
export default {
  data() {
    return {
      info: {
        question: "发热",
        goal: ["生命体征维持在正常范围", "半小时内降温到正常范围"],
        activity: [
          {
            name: "降温处理",
            method: [
              "冰袋冷敷头部",
              "药物或物理降温半小时后，应测量体温，并作好记录"
            ]
          },
          {
            name: "加强观察",
            method: [
              "每隔4小时测温一次，体温恢复正常3日后，改为每日1～2次",
              "监测病人体温，并作好记录"
            ]
          }
        ],
        measure: [
          {
            title: "降温处理",
            name: [
              "prn&nbsp;|&nbsp;冰袋冷敷头部",
              "prn&nbsp;|&nbsp;药物或物理降温半小时后，应测量体温，并作好记录"
            ]
          },
          {
            title: "加强观察",
            name:
              "bid&nbsp;|&nbsp;08:00/16:00&nbsp;每隔4小时测温一次，体温恢复正常3日后，改为每日1～2次"
          }
        ],
        actual: [
          "08:20 每隔4小时测温一次，体温恢复正常3日后，改为每日1～2次",
          "08:25 翻身",
          "14:00 冰袋冷敷头部",
          "16:00 对病人实施心电监护，并设定报警参数",
          "16:25 翻身",
          "17:00 健康教育"
        ]
      }
    };
  },

  mounted() {},

  methods: {
    colspanMethod: function({ row, column, rowIndex, columnIndex }) {
      //row:行对象，带有一行所有数据，column:列对象
      //rowIndex:行索引，columnIndex:列索引
      //加载表格时从（0，0）开始，（0，1）···（1，0）,(1,1)···依次获取数据
      if (columnIndex === 2) {
        //每次走到第3列时给单元格加上rowspan和colspan属性
        const _row = this.spanArr[rowIndex]; //从处理完的数组里获取
        const _col = _row > 0 ? 1 : 0;
        return {
          rowspan: _row,
          colspan: _col //相当于给给表格加上rowspan,colspan属性
        };
      }
    },

    //由于数据是动态的，所以页面加载时需要调用下面的方法，根据后台数据处理以知道要合并的行/列
    //得到的spanArr数组表示某一行所需要合并的列数
    getSpanArr: function(data) {
      this.spanArr = []; //定义在vue的data中
      if (data == null) {
        return;
      }
      for (var i = 0; i < data.length; i++) {
        if (i === 0) {
          this.spanArr.push(1);
          this.pos = 0;
        } else {
          if (data[i].ORGNAME === data[i - 1].ORGNAME) {
            this.spanArr[this.pos] += 1;
            this.spanArr.push(0);
          } else {
            this.spanArr.push(1);
            this.pos = i;
          }
        }
      }
    }
  }
};
</script>



<style type="text/css" lang="scss" scoped>
</style>

