<template>
  <div class="container-water-fall">
    <section>
      <h2>课堂作品</h2>
      <a>上传作品</a>
    </section>
    <div class="head">
      <h3>当前课时：<span>课时1名称</span></h3>
      <div>
        <el-select class="search" size="mini" v-model="value" placeholder="请选择">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value">
          </el-option>
        </el-select>
        <el-select class="search" size="mini" v-model="value" placeholder="请选择">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value">
          </el-option>
        </el-select>
        <el-select class="search" size="mini" v-model="value" placeholder="请选择">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value">
          </el-option>
        </el-select>
      </div>
    </div>
    <waterfall :col='col' :gutterWidth="gutterWidth"  :data="data"  @loadmore="loadmore"  v-loading="loading">
      <template >
        <div class="cell-item" v-for="(item,index) in data" :key="index">
          <div>
            <img :src="item.img"  />
            <div class="item-body">
              <div class="item-desc">{{item.title}}</div>
              <div class="task-name">{{item.user}}</div>
              <div class="name">课时1：课时名称</div>
              <div class="dianzan">
                <div class="head">
                  <span><img src="../../assets/images/head.png" alt=""></span>
                  <span>余周周</span>
                </div>
                <div>
                  <span>点赞</span>
                  <span>6</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </template>
    </waterfall>
    <button  @click="loadmore">加载更多</button>
  </div>
</template>

<script>
// import waterfall from 'vue-waterfall2'
import pic1 from '../../assets/images/pic1.png'
import pic2 from '../../assets/images/pic2.png'
import pic3 from '../../assets/images/pic3.png'
import pic4 from '../../assets/images/pic4.png'
import pic5 from '../../assets/images/pic5.png'
import pic6 from '../../assets/images/pic6.png'
import pic8 from '../../assets/images/pic8.png'
export default{
  data () {
    return {
      data: [],
      loading: true,
      col: 5,
      value: '',
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
      }]
    }
  },
  // components: {
  //   waterfall
  // },
  created () {
    setTimeout(() => {
      this.loading = false
      this.loadmore()
      this.loadmore()
    }, 1000)
  },
  computed: {
    itemWidth () {
      return (138 * 0.5 * (document.documentElement.clientWidth / 375))
    },
    gutterWidth () {
      return (9 * 0.5 * (document.documentElement.clientWidth / 375))
    }
  },
  methods: {
    mix () {
      this.$waterfall.mix()
    },
    switchCol (col) {
      this.col = col
      console.log(this.col)
    },
    loadmore (index) {
      console.log(index)
      let arr = [
        {
          img: pic1,
          title: '作品名称作品名称.jpg',
          avatar: '33',
          user: '任务名称：完成课时测试',
          liked: '12'
        },
        {
          img: pic2,
          title: 'wewq',
          avatar: '33',
          user: '33',
          liked: '12'
        },
        {
          img: pic3,
          title: '33333',
          avatar: '33',
          user: '33',
          liked: '12'
        },
        {
          img: pic4,
          title: 'wewq',
          avatar: '33',
          user: '33',
          liked: '12'
        },
        {
          img: pic5,
          title: '33333',
          avatar: '33',
          user: '33',
          liked: '12'
        },
        {
          img: pic6,
          title: '33333',
          avatar: '33',
          user: '33',
          liked: '12'
        },
        {
          img: pic8,
          title: '33333',
          avatar: '33',
          user: '33',
          liked: '12'
        }
      ]
      this.data = this.data.concat(arr)
    }
  }
}
</script>

<style lang="scss" scoped>
.container-water-fall{
  padding-left: 20px;
  padding-right: 10px;
  background-color: #fff;
  border-radius: 6px;
  margin-top: 20px;
  padding-bottom: 20px;
  &>section {
    display: flex;
    margin-right: 10px;
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
        background-image: url('../../assets/images/icon/icon_mycourse.png');
      }
    }
    a {
      width: 120px;
      height: 40px;
      cursor: pointer;
      line-height: 40px;
      margin-top: 15px;
      color: #fff;
      text-align: center;
      border-radius: 20px;
      background-color: #F79727;
    }
  }
  .head{
    height: 58px;
    line-height: 58px;
    display: flex;
    margin-right: 10px;
    h3{
      color: #888;
      flex: 1;
      span{
        color:#333;
        font-weight: 600;
      }
    }
  }
  &>button {
    display: block;
    width: 120px;
    height: 34px;
    line-height: 34px;
    text-align: center;
    margin: 0 auto;
    background-color: #fff;
    border: 1px solid #ccc;
    border-radius: 17px;
    margin-top: 20px;
    color: #999;
    font-size: 13px;
    font-family: '微软雅黑';
    cursor: pointer;
  }
  .cell-item {
    padding-right: 10px;
    margin-bottom: 10px;
    .item-body{
      padding: 11px;
      .item-desc{
        font-size: 13px;
        line-height: 14px;
        margin-bottom: 10px;
      }
      .task-name{
        font-size: 13px;
        color:#999;
        margin-bottom: 10px;
      }
      .name {
        background-color: #FFF2E5;
        display: inline-block;
        height: 24px;
        line-height: 24px;
        padding: 0 10px;
        color: #F79727;
        margin-bottom: 10px;
      }
      .dianzan{
        display: flex;
        .head{
          float: 1;
          display: flex;
          span:nth-child(1){
            display: inline-block;
            width: 30px;
            border-radius: 50%;
            overflow: hidden;
          }
        }
      }
    }
  }
}
.vue-waterfall-column img{
  width: 100%;
}
.cell-item>div{
  border-radius:4px;
  border:1px solid rgba(228,232,237,1)
}
</style>
