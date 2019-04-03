<template>
	<div class="team" v-loading="loading">
        <el-dialog :visible.sync="state" width="1100px" :before-close="handleClose">
			<span slot="title" class="teamTitle">
				<h3>学习小组<small>班级人数20人</small></h3>
			</span>
			<div class="group">
				<div class="transferFrom">
					<div class="pre"><img :src="trg" /></div>
					<ul>
						<li v-for="(item, index) in data" v-if="index < 7">
							<div class="teamAvatar">
								<img :src="head" />
								<span>欧阳娜娜</span>
								<p>
									<img :src="tteam1" />
									<img :src="tteam2" />
									<img :src="tteam3" />
								</p>
							</div>
						</li>
					</ul>
					<div class="next"><img :src="tn" /></div>
				</div>
				<div class="transferTo">
					<div class="pre"><img :src="trg" /></div>
					<ul>
						<li class="active">
							<h4>09级2班  01组</h4>
							<div class="classlist">
								<ul>
									<li v-for="(item, index) in 12" >
										<div class="teamAvatar">
											<img :src="head" />
											<span>欧阳娜娜</span>
										</div>
									</li>
								</ul>
							</div>
						</li>	
						<li>
							<h4>09级2班  01组 <i></i></h4>
							<div class="classlist">
								<ul>
									<li v-for="(item, index) in 12" >
										<div class="teamAvatar">
											<img :src="head" />
											<span>欧阳娜娜</span>
										</div>
									</li>
								</ul>
							</div>
						</li>	
						<li>
							<h4>09级2班  01组</h4>
							<div class="classlist">
								<ul>
									<li v-for="(item, index) in 12" >
										<div class="teamAvatar">
											<img :src="head" />
											<span>欧阳娜娜</span>
										</div>
									</li>
								</ul>
							</div>
						</li>	
					</ul>
					<div class="next"><img :src="tng" /></div>
				</div>
				<div class="stepbut">
					<button class="active">提交</button>
					<button>重置</button>
				</div>
			</div>
        </el-dialog>
	</div>
</template>

<script>
import head from 'assets/images/head.png'
import tteam1 from 'assets/images/tteam1.png'
import tteam2 from 'assets/images/tteam2.png'
import tteam3 from 'assets/images/tteam3.png'
import trg from 'assets/images/trg.png'
import tn from 'assets/images/tn.png'
import tng from 'assets/images/tng.png'

export default {
    name: "team",
    props:['state'],
	components: {
		
	},
	data() {
		return {
            loading: true,
			head,
			data: [1,2,3,4,5,6,7],
			tteam1,
			tteam2,
			tteam3,
			trg,
			tn,
			tng
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
.team {
	.teamTitle {
		font-size:16px;
		font-weight:bold;
		color:rgba(51,51,51,1);
		position: relative;
		text-indent: 15px;
		border-bottom: #E4E8ED 1px solid;
		width: 100%;
		display: inline-block;
		padding-bottom: 20px;
		h3 {
			font-weight: bold;
			&:after {
				content: '';
				display: block;
				width: 4px;
				height: 16px;
				background-color: #F79727;
				border-radius: 2px;
				position: absolute;
				left: 0;
				top: 0;
			}
			small {
				color: #F79727;
				font-size: 14px;
				font-weight: normal;
				margin-left: 25px;
			}
		}
	}
	.group {
		.teamAvatar {
			margin-top: 15px;
			img { width: 50px; height: 50px; border-radius: 100%}
			span {
				color: #333;
				font-size: 14px;
				display: block;
				margin-top: 10px;
				font-weight: bold;
			}
			p {
				margin-top: 20px;
				img {width: auto; height: auto;margin: 0 3px;}
			}
		}

		.transferFrom {
			position: relative;
			margin: 0 20px;
			ul{
				margin-left: 50px;
				li {
					width:126px;
					height:146px;
					border:1px solid rgba(228,232,237,1);
					border-radius:4px;
					text-align: center;
					display: inline-block;
					margin: 0 5px;
				}
			}
			.pre {
				top: 50px;
				left: 0;
			}
			.next {
				top: 50px;
				right: 0;
			}
		}

		.transferTo {
			margin: 20px 20px 0 20px;
			position: relative;
			&>ul {
				margin-left: 50px;
				&>li {
					width: 308px;
					height: 270px;
					border: #E4E8ED 1px solid;
					margin: 0 5px;
					display: inline-block;
					h4 {
						background: #F5F6F8;
						height: 50px;
						line-height: 50px;
						color: #333;
						font-size: 14px;
						padding-left: 20px;
						i {
							width: 19px;
							height: 12px;
							display: inline-block;
							margin-left: 5px;
							background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABMAAAAMCAIAAAAPshHVAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyFpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNS1jMDE0IDc5LjE1MTQ4MSwgMjAxMy8wMy8xMy0xMjowOToxNSAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIChXaW5kb3dzKSIgeG1wTU06SW5zdGFuY2VJRD0ieG1wLmlpZDpBRkIxQzcyQjU2MDgxMUU5QjRDNzg1Rjg5MzIzODZGQiIgeG1wTU06RG9jdW1lbnRJRD0ieG1wLmRpZDpBRkIxQzcyQzU2MDgxMUU5QjRDNzg1Rjg5MzIzODZGQiI+IDx4bXBNTTpEZXJpdmVkRnJvbSBzdFJlZjppbnN0YW5jZUlEPSJ4bXAuaWlkOkFGQjFDNzI5NTYwODExRTlCNEM3ODVGODkzMjM4NkZCIiBzdFJlZjpkb2N1bWVudElEPSJ4bXAuZGlkOkFGQjFDNzJBNTYwODExRTlCNEM3ODVGODkzMjM4NkZCIi8+IDwvcmRmOkRlc2NyaXB0aW9uPiA8L3JkZjpSREY+IDwveDp4bXBtZXRhPiA8P3hwYWNrZXQgZW5kPSJyIj8+a3kwqwAAALlJREFUeNpi3Hnw5Oev3xhwAw52NntzQyYmJjRxFhEhATY2Vjw6uTg4GBmZMMUZv377wUAWYCJe6fcfPx89e/n//3+SdX75+u3qrXvHzl7+9PkryLWHT13EH0Kc7Oym+pqMjIyv374/c/kGSA8jo5KcFBMDuYDFSEedJA18PNy66sp8vNwkhC0whF6/+yArKQZ0LUWxwnLj7sNPX77iTwnaakpga1B1vnn3AX/YfmX//v//P8xkBBBgACDqRa/HaUGmAAAAAElFTkSuQmCC)
						}
					}
					ul{
						margin: 0 10px;
						li {
							display: inline-block;
							width: 70px;
							text-align: center;
						}
					}
					&.active {
						h4 {
							background: #FFF3E5;
						}
					}
				}
			}
			.classlist {
				overflow-y: scroll;
				height: 220px;
			}
			.pre {
				top: 50%;
				margin-top: -17px;
				left: 0;
			}
			.next {
				top: 50%;
				margin-top: -17px;
				right: 0;
			}
		}
		.pre, .next {
			position:absolute;
			img {
				width: auto;
			}
		}
		.stepbut {
			margin-top: 40px;
			width: 100%;
			text-align: center;
			button {
				margin: 0 20px;
				cursor: pointer;
				width:150px;
				height:40px;
				border-radius:20px;
				font-size: 16px;
				border:1px solid rgba(204,204,204,1);
				background: transparent;
				color: #999;
			}
			.active {
				border:none;
				background:#F79727;
				color: #fff;
			}
		}
	}
}
</style>
