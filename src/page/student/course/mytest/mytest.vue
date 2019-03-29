<template>
  <div class="mytest"  v-loading="loading">
    <section>
      <h2>我的测试</h2>
      <el-select class="search" v-model="value" placeholder="请选择">
        <el-option
          v-for="item in options"
          :key="item.value"
          :label="item.label"
          :value="item.value">
        </el-option>
      </el-select>
    </section>
    <div>
      <section>
        <ul>
          <li v-for="(n, index) in 3" :key="index">
            <p>3.5 <span>分</span></p>
            <p class="title">自我认知</p>
            <div><span>班级平均</span><span>3.2</span></div>
            <div><span>班级平均</span><span>3.2</span></div>
            <section>分数说明</section>
          </li>
        </ul>
        <el-table
          :data="tableData"
          style="width: 100%"
          @row-click="cellEnter"
          :default-sort = "{prop: 'date', order: 'descending'}"
          row-class-name="tableRow"
          >
          <el-table-column
            label="课时名称"
            sortable
            align="center"
            width="180">
            <template slot-scope="scope">
              <span style="margin-left: 10px">{{ scope.row.address }}</span>
              <p class="look">查看明细 ></p>
            </template>
          </el-table-column>
          <el-table-column
            prop="name"
            label="技能维度"
            sortable
            align="center"
            width="180">
          </el-table-column>
          <el-table-column
            prop="date"
            label="完成时间"
            align="center">
          </el-table-column>
          <el-table-column
            prop="name"
            label="分数"
            align="center"
            sortable>
          </el-table-column>
          <el-table-column
            prop="name"
            label="总分"
            align="center"
            sortable>
          </el-table-column>
        </el-table>
      </section>
      <aside>
        <h3>测试完成率</h3>
        <el-progress type="circle" :stroke-width="8" :width="120" color="#26BF73" :percentage="pro1" status="text"><p class="num">{{pro1}}%</p><p class="font">我的完成率</p></el-progress>
        <el-progress type="circle" :stroke-width="8" :width="120" color="#FF9C19" :percentage="pro2" status="text"><p class="num">{{pro2}}%</p><p class="font">班级平均</p></el-progress>
        <el-progress type="circle" :stroke-width="8" :width="120" color="#FF9C19" :percentage="pro3" status="text"><p class="num">{{pro3}}%</p><p class="font">年级平均</p></el-progress>
      </aside>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Mytest',
  data () {
    return {
      loading: true,
      pro1: 0,
      pro2: 0,
      pro3: 0,
      options: [{
        value: '选项1',
        label: '课程1'
      }, {
        value: '选项2',
        label: '课程2'
      }, {
        value: '选项3',
        label: '课程3'
      }, {
        value: '选项4',
        label: '课程4'
      }, {
        value: '选项5',
        label: '课程5'
      }],
      value: '课程1',
      tableData: [{
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江'
      }, {
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路'
      }, {
        date: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路'
      }, {
        date: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路'
      }]
    }
  },
  created () {
    setTimeout(() => {
      this.loading = false
      this.pro1 = 80
      this.pro2 = 75
      this.pro3 = 60
    }, 1000)
  },
  methods: {
    formatter (row, column) {
      return row.address
    },
    cellEnter (row) {
      console.log(1)
    }
  }
}
</script>

<style lang="scss" scoped>
.mytest{
  margin: 14px 14px 14px 0;
  background-color: #fff;
  border-radius: 6px;
  padding: 0 20px;
  &>section {
    display: flex;
    height: 70px;
    line-height: 70px;
    border-bottom: 1px solid #E4E8ED;
    h2{
      flex: 1;
      display: block;
      height: 20px;
      text-indent: 40px;
      position: relative;
      font-size: 18px;
      font-weight: 600;
      &:after{
        content: '';
        position: absolute;
        width: 18px;
        height: 20px;
        top: 25px;
        left: 8px;
        background-image: url('../../../../assets/images/icon/icon_mycourse.png');
      }
    }
    .search {
      margin-right: 10px;
      width: 160px;
      height: 32px;
    }
  }
  &>div {
    margin-top: 20px;
    padding-bottom: 20px;
    overflow: hidden;
    aside {
      float: right;
      width: 189px;
      border-left: 1px solid #E4E8ED;
      text-align: center;
      h3 {
        margin: 14px 0 25px;
        font-weight: 600;
        font-size: 17px;
      }
      &>div{
        margin-bottom: 40px;
      }
      .num{
        font-size: 28px;
        line-height: 28px;
        font-weight: 600;
        margin-bottom: 12px;
        color: #333;
        font-family: 'DIN-Medium'
      }
      .font {
        color: #999;
        font-size: 13px;
        line-height: 13px;
      }
    }
    &>section{
      width: calc(100% - 210px);
      float: left;
      padding: 0 10px;
      margin-bottom: 30px;
      .look{
        color: #f80;
      }
      ul{
        width: 100%;
        display: flex;
        margin-bottom: 30px;
        justify-content: space-between;
        li{
          width: 250px;
          // background-color: #3EACFA;
          border-radius:6px;
          overflow: hidden;
          background:linear-gradient(-45deg,#2D98F8,#3CAAFA);
          position: relative;
          p:nth-child(1) {
            font-size: 40px;
            line-height: 40px;
            color: #fff;
            margin: 28px 0 0 20px;
            span{
              font-size: 14px;
            }
          }
          &>.title {
            margin-left: 20px;
            color: #fff;
            margin-bottom: 28px;
          }
          &>div{
            height: 14px;
            line-height: 14px;
            margin-bottom: 10px;
            color: #D0E6FD;
            padding:0 20px;
            display: flex;
            span:nth-child(1){
              flex: 1;
              display: block;
              text-indent: 13px;
              position: relative;
              &:after{
                content: '';
                position: absolute;
                width: 4px;
                height: 4px;
                left: 0;
                top: 5px;
                background: #D0E6FD;
              }
            }
          }
          &>section{
            height: 40px;
            line-height: 40px;
            margin-top: 8px;
            background: #2286F6;
            text-indent: 20px;
            color: #D0E6FD;
            font-size: 13px;
          }
          &:nth-child(2){
            background:linear-gradient(-45deg,#22BB8E,#4DD3B1);
            &>section{
              background: #1CB181;
            }
            &:after{
              top: 22px;
              background-image: url('../../../../assets/images/icon/icon_test_gh.png');
            }
          }
          &:nth-child(3){
            background:linear-gradient(-45deg,#F39A28,#F9C162);
            &>section{
              background: #F29124;
            }
            &:after{
              top: 22px;
              background-image: url('../../../../assets/images/icon/icon_test_ts.png');
            }
          }
          &:after {
            content: '';
            display: block;
            width: 66px;
            height: 66px;
            position: absolute;
            right: 0;
            top: 0;
            background-repeat: no-repeat;
            opacity: .5;
          }
          &:nth-child(1){
            &:after{
              width: 61px;
              height: 67px;
              top: 21px;
              background-image: url('../../../../assets/images/icon/icon_test_rz.png');
            }
          }
        }
      }
    }
  }
}
</style>
