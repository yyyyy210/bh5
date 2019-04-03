<template>
	<div class="classopen" v-loading="loading">
        <el-dialog :visible.sync="state" width="520px" :before-close="handleClose">
			<span slot="title" class="title">
				<h3>开放课件</h3>
				<div class="search">
					<input placeholder="搜索班级"/>
					<i class="el-icon-search"></i>
				</div>
			</span>
			<div class="group">
				<ul class="classList">
					<li><div>高三物理</div><div><img :src="classin" /></div></li>
					<li><div>高三物理</div><div><img :src="classstart" /></div></li>
					<li><div>高三物理</div><div><img :src="classstart" /></div></li>
					<li><div>高三物理</div><div><img :src="classstart" /></div></li>
					<li><div>高三物理</div><div><img :src="classstart" /></div></li>
					<li><div>高三物理</div><div><img :src="classstart" /></div></li>
					<li><div>高三物理</div><div><img :src="classin" /></div></li>
				</ul>
				<div class="stepbut">
					<button class="pre active">上一页</button>
					<button class="next">下一页</button>
				</div>
			</div>
        </el-dialog>
	</div>
</template>

<script>
import classin from 'assets/images/classin.png'
import classstart from 'assets/images/classstart.png'
export default {
    name: "classopen",
    props:['state'],
	components: {

	},
	data() {
		return {
			loading: true,
			classin,
			classstart
		};
	},
	created() {
		let _this = this;
		setTimeout(() => {
			_this.loading = false;
		}, 1000);
	},
	methods: {
        handleClose() {
            this.$emit('close');
        }
    }
};
</script>

<style lang="scss" scoped>
.classopen {
	.title {
		font-size:16px;
		font-weight:bold;
		color:rgba(51,51,51,1);
		position: relative;
		text-indent: 15px;
		border-bottom: #E4E8ED 1px solid;
		width: 100%;
		display: inline-block;
		padding-bottom: 20px;
		position: relative;
		h3 {
			font-weight: bold;
			// &:after {
			// 	content: '';
			// 	display: block;
			// 	width: 4px;
			// 	height: 16px;
			// 	background-color: #F79727;
			// 	border-radius: 2px;
			// 	position: absolute;
			// 	left: 0;
			// 	top: 0;
			// }
		}
		.search {
			width:286px;
			height:38px;
			background:rgba(238,238,238,1);
			border-radius: 20px;
			font-weight: normal;
			position: absolute;
			top: -10px;
			left: 150px;
			input {
				font-size: 14px;
				height: 38px;
				width: 210px;
				background: transparent;
			}
			i {
				color: #ccc;
				font-size: 17px;
				cursor: pointer;
			}
			
		}
	}
	.group {
		margin-top: -20px;
		.classList {
			li {
				display: flex;
				div {
					flex: 1;
					text-align: center;
					height: 50px;
					line-height: 50px;
				}
				&:nth-child(odd) {
					background:rgba(245,246,247,1);
				}
				&:nth-child(even), &:hover {
					background:rgba(255,255,255,1);
				}
			}
			img {width: auto;}
		}
		.stepbut {
			margin-top: 20px;
			width: 100%;
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
		}
	}
}
</style>
