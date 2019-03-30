<template>
	<div class="details" v-loading="loading">
        <el-dialog :visible.sync="state" width="80%" :before-close="handleClose">
			<div slot="title" class="detailsHead">
                <div class="avatar"><img :src="head" /></div>
                <div class="name">
                    <h3>课程作品文件名称课程作品文件名称.pdf</h3>
                    <span><var>156.33kb</var><time>更新时间：2019.3.14 16:32</time></span>
                </div>
                <div class="but">
                    <span><img class="bimg39" :src="icon_39" />删除</span>
                    <span><img class="bimg40" :src="icon_40" />下载</span>
                    <span><img class="bimg42" :src="icon_42" />添加到成长档案</span>
                </div>
			</div>
			<div class="group">
                <div><img :src="details1" /></div>
                <div><img :src="details1" /></div>
                <div>课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称课程作品文件名称</div>
                <video controls>
                    <source :src="movie1"  type="video/mp4">
                </video>
			</div>
        </el-dialog>
	</div>
</template>

<script>
import details1 from 'assets/images/details1.png'
import movie1 from 'assets/images/movie.mp4'
import head from 'assets/images/head.png'
import icon_39 from 'assets/images/icon/icon_39.png'
import icon_40 from 'assets/images/icon/icon_40.png'
import icon_42 from 'assets/images/icon/icon_42.png'

export default {
    name: "details",
    props:['state'],
	components: {
		
	},
	data() {
		return {
            loading: true,
            details1,
            head,
            icon_39,
            icon_40,
            icon_42,
            movie1
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
.details {
    img {width: auto;}
    .detailsHead {
        display: flex;
        border-bottom: #E4E8ED 1px solid;
        margin: -10px -20px -10px;
        padding-bottom: 10px;
        .avatar {
            flex: 1;
            max-width: 60px;
            margin-left: 20px;
            img { width: 50px; height: 50px; border-radius: 100%}
        }

        .name {
            flex: 1;
            font-size: 14px;
            h3{color: #333; font-weight: bold; margin: 5px 0 10px 0;}
            span {
                color: #999;
                time {margin-left: 10px;}
            }
        }

        .but {
            flex: 1;
            text-align: right;
            margin-right: 50px;
            margin-top: 15px;
            span {
                color: #666;
                font-size: 14px;
                margin-right: 25px;
                cursor: pointer;
            }
            img {
                height: 20px;
                margin-right: 10px;
            }
            .bimg39 {width: 15px;}
            .bimg40 {width: 16px;}
            .bimg42 {width: 20px;}
        }
    }

    .group {
        overflow-x: scroll;
        max-height: 600px;
        margin-top: -30px;
        margin-bottom: -30px;
        text-align: center;
        border-left:1px solid rgba(228,232,237,1);
        border-right:1px solid rgba(228,232,237,1);

        video{
            width: 80%;
        }
    }
}
</style>
