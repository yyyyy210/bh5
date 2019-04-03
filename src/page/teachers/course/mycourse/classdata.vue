<template>
	<div class="classdata" v-loading="loading">
        <el-dialog :visible.sync="state" width="80%" :before-close="handleClose" top="7vh">
			<span slot="title" class="title">
				<h3>备课资料</h3>
			</span>
			<div class="group">
            <section>
                <ul>
                    <li v-for="(item) in [img1,img2,img3,img4,img5,img1,img2,img3,img4,img5,img1,img2,img3,img4,img5]">
                        <div class="but">
                            <span><img :src="classLook" alt=""></span>
                            <span><img :src="classdown" alt=""></span>
                        </div>
                        <img :src="item" alt="">
                        <h4>课程名称课程名称</h4>
                        <p class="time">2019/01/01</p>
                        <p class="teacher">刘云霞老师</p>
                    </li>
                </ul>
            </section>
			</div>
        </el-dialog>
	</div>
</template>

<script>
import img1 from 'assets/images/img1.png'
import img2 from 'assets/images/img2.png'
import img3 from 'assets/images/img3.png'
import img4 from 'assets/images/img4.png'
import img5 from 'assets/images/img5.png'
import classLook from 'assets/images/classLook.png'
import classdown from 'assets/images/classdown.png'

export default {
    name: "classdata",
    props:['state'],
	components: {
		
	},
	data() {
		return {
            loading: true,
            img1,
            img2,
            img3,
            img4,
            img5,
            classLook,
            classdown
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
.classdata {
	.title {
		font-size:16px;
		font-weight:bold;
		color:rgba(51,51,51,1);
		position: relative;
		text-indent: 15px;
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
		}
	}
	.group {
        overflow-x: hidden;
        overflow-y: scroll;
        max-height: 650px;
        section {
            padding-bottom: 30px;
            ul{
                display: flex;
                display: -webkit-flex;
                justify-content: space-between;
                flex-direction: row;
                flex-wrap: wrap;
                li{
                    width: 190px;
                    border-radius:4px;
                    overflow: hidden;
                    border:1px solid rgba(228,232,237,1);
                    margin-bottom: 20px;
                    padding-bottom: 3px;
                    cursor: pointer;
                    position: relative;
                    h4{
                        margin: 16px 13px 15px;
                        font-size: 15px;
                        font-weight: 600;
                    }
                    p{
                        display: block;
                        height: 12px;
                        margin-left: 13px;
                        margin-bottom: 9px;
                        font-size: 12px;
                        line-height: 12px;
                        text-indent: 20px;
                        position: relative;
                        &.time:after  {
                            content: '';
                            display: block;
                            width: 12px;
                            height: 12px;
                            background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAwAAAAMCAIAAADZF8uwAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyFpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNS1jMDE0IDc5LjE1MTQ4MSwgMjAxMy8wMy8xMy0xMjowOToxNSAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIChXaW5kb3dzKSIgeG1wTU06SW5zdGFuY2VJRD0ieG1wLmlpZDo3MkI3NURBRDU1RjkxMUU5OTZDQzhGQjEzRkEyRTAxRSIgeG1wTU06RG9jdW1lbnRJRD0ieG1wLmRpZDo3MkI3NURBRTU1RjkxMUU5OTZDQzhGQjEzRkEyRTAxRSI+IDx4bXBNTTpEZXJpdmVkRnJvbSBzdFJlZjppbnN0YW5jZUlEPSJ4bXAuaWlkOjcyQjc1REFCNTVGOTExRTk5NkNDOEZCMTNGQTJFMDFFIiBzdFJlZjpkb2N1bWVudElEPSJ4bXAuZGlkOjcyQjc1REFDNTVGOTExRTk5NkNDOEZCMTNGQTJFMDFFIi8+IDwvcmRmOkRlc2NyaXB0aW9uPiA8L3JkZjpSREY+IDwveDp4bXBtZXRhPiA8P3hwYWNrZXQgZW5kPSJyIj8+U38wGgAAAS5JREFUeNpkUMGqgkAUnZnMytR1lLgIRMSdBgZ9dPgP4UIoWqhBLiJKMLdFaZF23huePOis7rlz59xzLm2ahhDyfD7X6/Xr9RIEgVKKotvtOo7T6/XwSjFUFEUQBJqmmaapKAq6t9ttv9+fTifP80ajEXk8Hr7vH4/H5gtZli2Xy+v1yrbbLTR0XSe/wDS+8Xo8Hk+n081mw+73u2VZ5A+73a4dAmzbruuaiaI4GAzaLmMMIWD8/X6DdjodSZIEnq6FqqpRFCHjZDIxDIM3haqqyrLs9/ucz+dzUMjgBKAokJRhVxzH/8XwYTgcwgZqqMIAw8WQ6Hw+ky9cLpc0TV3X/Tlmnuer1QpXQBZo4BmRkyQ5HA6LxQKHoNw4YodhCAc8KSiWzGYzWZZBPwIMACPsrlMMRFcqAAAAAElFTkSuQmCC);
                            position: absolute;
                            left: 0;
                            top: 0;
                        }
                        &.teacher:after {
                            content: '';
                            display: block;
                            width: 12px;
                            height: 14px;
                            background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAwAAAAOCAIAAACU32q7AAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyFpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNS1jMDE0IDc5LjE1MTQ4MSwgMjAxMy8wMy8xMy0xMjowOToxNSAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIChXaW5kb3dzKSIgeG1wTU06SW5zdGFuY2VJRD0ieG1wLmlpZDo4MDM0REEwQjU1RjkxMUU5OTM5NkI5OEZBM0I0QjcyNyIgeG1wTU06RG9jdW1lbnRJRD0ieG1wLmRpZDo4MDM0REEwQzU1RjkxMUU5OTM5NkI5OEZBM0I0QjcyNyI+IDx4bXBNTTpEZXJpdmVkRnJvbSBzdFJlZjppbnN0YW5jZUlEPSJ4bXAuaWlkOjgwMzREQTA5NTVGOTExRTk5Mzk2Qjk4RkEzQjRCNzI3IiBzdFJlZjpkb2N1bWVudElEPSJ4bXAuZGlkOjgwMzREQTBBNTVGOTExRTk5Mzk2Qjk4RkEzQjRCNzI3Ii8+IDwvcmRmOkRlc2NyaXB0aW9uPiA8L3JkZjpSREY+IDwveDp4bXBtZXRhPiA8P3hwYWNrZXQgZW5kPSJyIj8+NwbFUQAAATBJREFUeNp0kLGrglAUxvVpgSBUg0OEi6CBLUEugv+tkzqIi4uDGDSKexI5SEtDkgWpqX1l9HwP+g33nnPvd8653yXbtiVeXC6XIAjqukaMQ1mWRVHsruhuy7LMtu35fL5cLgeDwX6/R0FZlovFguiKgOM46/W67YEyXdev1yviH+hutxtWVVWJHqPRiOO47XaL+Cm63+/0C+IvFEUVRfEWsSyLtnEc/xMdj0dBEN4isFqtfN9P07RL0cA0zel0iolIyc8XwFEURePxmCRJfMdkMtE0rbv6FYHz+YyhVVXNZjOe5z/nT9HhcAjDEMFwOGQYBp0wDpZhCFJFUegkSTzPg3/kMNhvfDqdNptNnueEZVm73a79jmEYdNM08Nlv0AejJUmi8Q7Xdb+JAHw8BBgA2CrMp9vJ4jMAAAAASUVORK5CYII=);
                            position: absolute;
                            left: 0;
                            top: 0;
                        }
                    }
                    &.bai{
                        visibility: hidden;
                        height: 0;
                    }
                    .but {
                        position: absolute;
                        top: 20px;
                        width: 100%;
                        left: 0;
                        right: 0;
                        display: none;
                        span {
                            margin: 10px 0;
                            display: block;
                            text-align: center;
                            img {
                                width: auto;
                            }
                        }
                    }
                    &:hover {
                        .but{
                            display: block;
                        }
                    }
                }
            }
        }
    }
}
</style>
