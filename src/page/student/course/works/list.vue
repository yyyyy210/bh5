<template>
  <div class="container-tends">
    <section>
      <h2>课堂作品</h2>
      <div class="teandsearch">
        <a class="upload" @click="changeUpload"><img :src="icon_task_close" />上传作品</a>
      </div>
    </section>
    <div class="head">
      <h3>当前课时：<span>课时1名称</span></h3>
      <div>
        <el-select class="search" v-model="value" placeholder="课时">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value">
          </el-option>
        </el-select>
        <el-select class="search"  v-model="value" placeholder="课程筛选">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value">
          </el-option>
        </el-select>
        <el-select class="search"  v-model="value" placeholder="作品分类">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value">
          </el-option>
        </el-select>
        <el-select class="search"  v-model="value" placeholder="班级筛选">
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
            <div class="taskimg">
              <img :src="item.img" />
              <div class="but">
                <el-tooltip effect="dark" content="删除" placement="top">
                  <i><img :src="icon_39" /></i>
                </el-tooltip>
                <el-tooltip effect="dark" content="下载" placement="top">
                  <i><img :src="icon_40" /></i>
                </el-tooltip>
                <el-tooltip effect="dark" content="添加" placement="top">
                  <i><img :src="icon_42" /></i>
                </el-tooltip>
              </div>
            </div>
            <div class="item-body" @click="changedetails">
              <div class="item-desc">{{item.title}}</div>
              <div class="task-name">{{item.user}}</div>
              <div class="name">课时1：课时名称</div>
              <div class="dianzan">
                <div class="head">
                  <span><img src="../../../../assets/images/head.png" alt=""></span>
                  <span class="tname">余周周</span>
                </div>
                <div class="good">
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

    <!--  -->
    <Details :state="detailsShow" v-on:close="changedetails" />
    <upload :state="uploadShow" v-on:close="changeUpload" />

  </div>
</template>

<script>
import Details from './details.vue'
import Upload from './upload.vue'
import pic1 from 'assets/images/pic1.png'
import pic2 from 'assets/images/pic2.png'
import pic3 from 'assets/images/pic3.png'
import pic4 from 'assets/images/pic4.png'
import pic5 from 'assets/images/pic5.png'
import pic6 from 'assets/images/pic6.png'
import pic8 from 'assets/images/pic8.png'
import icon_39 from 'assets/images/icon/icon_39.png'
import icon_40 from 'assets/images/icon/icon_40.png'
import icon_42 from 'assets/images/icon/icon_42.png'
import icon_task_close from 'assets/images/icon/icon_task_close.png'

export default{
	components: {
    Details,
    Upload
	},
  data () {
    return {
      icon_39,
      icon_40,
      icon_42,
      icon_task_close,
      detailsShow: false,
      uploadShow: false,
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
    },
    loadmore (index) {
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
    },
    changedetails(){
      this.detailsShow = !this.detailsShow;
    },
    changeUpload(){
      this.uploadShow = !this.uploadShow;
    }
  },
}
</script>

<style lang="scss" scoped>
.container-tends{
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
        background-image: url('../../../../assets/images/icon/icon_mycourse.png');
      }
    }
    .teandsearch {
      .el-input {
        float: left;
        width:242px;
        input.el-input__inner {
          width:242px;
          height:40px;
          background:rgba(238,242,245,1);
          border-radius:10px;
        }
      }
      a {
        float: left;
        height: 40px;
        cursor: pointer;
        line-height: 40px;
        margin-top: 15px;
        margin-left: 15px;
        color: #fff;
        text-align: center;
        border-radius: 20px;
        background-color: #F79727;
        padding: 0 20px;
      }
      .upload {
        img {
          width: 24px;
          height: 24px;
          transform: rotate(-90deg);
          margin-right: 10px;
        }
      }
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
    .search {
      width: 150px;
    }
    img {border-radius: 100%}
    .tname {margin-left: 5px}
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
        background-color: rgba(153,153,153,.1);
        display: inline-block;
        height: 24px;
        line-height: 24px;
        padding: 0 10px;
        font-weight:bold;
        color: rgba(153,153,153,1);
        margin-bottom: 10px;
      }
      .dianzan{
        display: flex;
        position: relative;
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
        .good {
          position: absolute;
          right: 0px;
          bottom: 20px
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

.taskimg {
  position: relative;
  .but {
    position: absolute;
    bottom: 10px;
    width: 100%;
    text-align: center;
    cursor: pointer;
    display: none;
    img {width: auto}
    i {
      background: #fff;
      width: 58px;
      height: 58px;
      line-height: 58px;
      text-align: center;
      border-radius: 100%;
      display: inline-block;
    }
  }
  &:hover {
    .but {
      display: block;
    }
  }
}
</style>
