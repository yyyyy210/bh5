<template>
	<div class="courseware" v-loading="loading">
		<div class="taskleft">
			<div class="backclass" @click="goback">< 返回课程</div>
			<div class="step">
				<div class="stepimg" v-if="page === 1">
					<img :src="material" />
				</div>
				<div class="stepimg" v-if="page === 2">
					<img :src="details1" />
				</div>
			</div>
			<div class="stepbut">
				<button class="pre" :class="{'active':page === 1}" @click="page = 1">上一页</button>
				<span class="pages"><var>{{page}}</var>/2</span>
				<button class="next" :class="{'active':page === 2}" @click="page = 2">下一页</button>
			</div>
			<div class="allprint" @click="screenF"><img :src="allprint" />{{fullShow ? '退出全屏' : '全屏' }}</div>
		</div>
        <hgroup>
            <div><span>本课时任务</span><span><img src="../../assets/images/icon/icon_task_close.png" alt=""></span></div>
            <ul class="task">
                <li>
                	<h4 class="icon-course">课件任务名称<span class="active">查看结果</span></h4>
                </li>
                <li>
                	<h4 class="icon-test">课件任务名称</h4>
                </li>
                <li>
                	<h4 class="icon-questionnaire">课件任务名称<span>查看结果</span></h4>
                </li>
                <li>
                	<h4 class="icon-works">课件任务名称<span>查看结果</span></h4>
                </li>
                <li>
                	<h4 class="icon-clock">课件任务名称<span>查看结果</span></h4>
                </li>
            </ul>
			<ul class="operation">
				<li class="edit"><span><i class="el-icon-check"></i>保存修改</span></li>
				<li class="add"><span><i class="el-icon-plus"></i>添加任务</span></li>
			</ul>
        </hgroup>
	</div>
</template>

<script>
import screenfull from 'screenfull'
import material from 'assets/images/student/material.png'
import details1 from 'assets/images/details1.png'
import allprint from 'assets/images/allprint.png'

export default {
	name: "tasks",
	components: {
		
	},
	data() {
		return {
            loading: true,
			material,
			details1,
			allprint,
			fullShow: false,
			page: 1
		};
	},
	created() {
		let _this = this;
		setTimeout(() => {
			_this.loading = false;
		}, 1000);
	},
	methods: {
		goback(){
			screenfull.exit()
			this.$router.go(-1)
		},
		screenF(){
			this.fullShow = !this.fullShow;
			screenfull.toggle()
		}
    }
};
</script>

<style lang="scss" scoped>
.courseware {
    background:rgba(255,255,255,1);
    border:1px solid rgba(228,232,237,1);
    border-radius:6px;
	padding: 5px 10px;
	display: flex;
	height: 100vh;
	position: relative;
	.taskleft{
		position: relative;
		flex: 1;
	}
    .step {
        background:rgba(255,255,255,1);
        border:1px solid rgba(228,232,237,1);
        border-radius:6px;
        margin: 15px;
		height: 94%;
        .stepimg {
			// width: 992px;
			text-align: center;
            img {
				width: auto;
				max-height: 600px;
			}
        }
    }
	.stepbut {
		position: absolute;
		bottom: 30px;
		left: 0;
		right: 0;
		margin: 0 auto;
		width: 50%;
		text-align: center;
		button {
			margin: 0 20px;
			cursor: pointer;
			width:170px;
			height:44px;
			border-radius:4px;
			font-size: 16px;
			border:1px solid rgba(0,0,0,1);
			background:linear-gradient(-90deg,rgba(255,183,38,1),rgba(255,129,38,1));
			border:none;
			color: #fff;
		}
		.active {
			background:transparent;
			border: rgba(255,129,38,1) 1px solid;
			color: #FF8126;
		}
		.pages {
			font-size: 12px;
			color: #666;
			var {color: #F79727;}
		}
	}
	.backclass {
		color: #666666;
		font-size: 16px;
		line-height: 30px;
		cursor: pointer;
	}
	.allprint {
		color: #666;
		font-size: 18px;
		position: absolute;
		right: 30px;
		bottom: 30px;
		z-index: 10;
		cursor: pointer;
		img {width: auto; margin-right: 10px;}
	}
}
hgroup{
	flex: 1;
	max-width: 275px;
    width: 275px;
    min-height: 700px;
    padding-bottom: 50px;
    float: right;
    border-left:1px solid rgba(228,232,237,1);
    transition: width .3s;
    background-color: #fff;
	position: relative;
    &>div{
      padding: 0 20px;
      height: 70px;
      line-height: 70px;
      background-image: url('../../assets/images/task_bg.png');
      display: flex;
      font-size: 18px;
      color: #fff;
      font-weight: 600;
      &>span:first-child{
        flex: 1;
      }
      &>span:nth-child(2) {
        display: inline-block;
        width: 24px;
        height: 24px;
        line-height: 24px;
        margin-top: 23px;
        cursor: pointer;
      }
    }
    &>ul>li{
      padding: 15px 14px 0 16px;
      h4{
        height: 16px;
        line-height: 16px;
        font-weight: 600;
        text-indent: 26px;
        background-size: 16px 16px;
        margin-bottom: 15px;
        background-position: 0 0;
        background-repeat: no-repeat;
        &.icon-course{
          background-image: url('../../assets/images/icon/icon_course_name.png');
        }
        &.icon-test{
          background-image: url('../../assets/images/icon/icon_course_content.png');
        }
        &.icon-questionnaire{
          background-size: 14px 16px;
          background-image: url('../../assets/images/icon/icon_course_look.png');
        }
        &.icon-works{
          background-size: 16px 14px;
          background-position: 1px 0;
          background-image: url('../../assets/images/icon/icon_course_completed.png');
        }
        &.icon-clock{
          background-image: url('../../assets/images/icon/icon_clock.png');
        }
      }
      div{
        background-color: #F2F5F7;
        padding: 15px 12px 3px;
        p{
          display: block;
          font-size: 12px;
          line-height: 12px;
          text-indent: 16px;
          position: relative;
          color: #888;
          margin-bottom: 11px;
          &:after {
            content: '';
            display: block;
            position: absolute;
            width: 4px;
            height: 4px;
            background-color: #C2C8CC;
            top: 3px;
            left: 0;
          }
        }
      }
    }
    &.active {
	max-width: 44px;
      width: 44px;
      height: 44px;
      min-height: 44px;
      padding-bottom: 0;
      margin-top: 28px;
      background-color: transparent;
      border: none;
      &>div{
        width: 44px;
        height: 44px;
        padding: 10px;
        text-align: center;
        border-radius: 50% 0 0 50%;
        span:nth-child(1){
          display: none;
        }
        span:nth-child(2){
          margin-top: 0;
          transform: rotate(180deg);
        }
      }
      ul{
        display: none;
      }
    }
	.task {
		span {
			float: right;
			border: 1px solid #ccc;
			border-radius: 4px;
			color: #ccc;
			font-weight: normal;
			text-indent: 0;
			display: inline-block;
			padding: 3px 10px;
			font-size: 12px;
			cursor: pointer;
			&.active {
				border:1px solid #F79727;
				color:#F79727;
			}
		}
	}
	.operation {
		position: absolute;
		bottom: 20px;
		left: 50px;
		span {
			border:2px solid rgba(187,187,187,1);
			border-radius:22px;
			color: #999;
			font-size: 16px;
			padding: 10px 20px;
			display: inline-block;
		}
		i {margin-right: 10px}
		.edit {
			span {
				border:2px solid rgba(247,151,39,1);
				color: #F79727;
			}
		}
		.add {

		}
	}
}
</style>
