<template>
	<div class="upload" v-loading="loading">
        <el-dialog :visible.sync="state" width="800px" :before-close="handleClose">
			<div slot="title" class="uploadHead">
                <h3>上传作品</h3>
			</div>
            <div>
                <el-form ref="form" :model="form" label-width="150px">
                    <el-form-item label="作品完成日期：">
                        <el-col :span="11">
                            <el-date-picker type="date" placeholder="选择日期" v-model="form.date" style="width: 100%;"></el-date-picker>
                        </el-col>
                    </el-form-item>
                    <el-form-item label="作品名称：">
                        <el-input v-model="form.name"></el-input>
                    </el-form-item>
                    <el-form-item label="作品介绍：">
                        <el-input type="textarea" v-model="form.desc" :rows="4" placeholder="用140字以内的描述来介绍你的作品"></el-input>
                    </el-form-item>
                    <el-form-item label="所属课程：">
                        <el-select v-model="form.cat1" placeholder="请选择课程">
                            <el-option label="课程一" value="1"></el-option>
                            <el-option label="课程二" value="2"></el-option>
                        </el-select>
                    </el-form-item>
                    <el-form-item label="作品归属：">
                        <el-select v-model="form.cat2" placeholder="请选择课作品归属">
                            <el-option label="小组" value="1"></el-option>
                            <el-option label="个人" value="2"></el-option>
                        </el-select>
                    </el-form-item>
                    <el-form-item label="粘贴URL链接：">
                        <el-input v-model="form.url"></el-input>
                    </el-form-item>
                    <el-form-item label="文件上传：">
                        <div class="uploadFile">
                            <span class="but"><img :src="icon_course_name" />点击上传</span>
                            <div class="picList">
                                <div  class="upok">已上传文件</div>
                                <ul>
                                    <li v-for="(item, index) in 5">
                                        <img src="https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100" />
                                    </li>
                                </ul>
                            </div>
                            <div class="changeUpdate">点击上传</div>
                            <div class="text">支持PDF,word，图片格式，PPT，视频上传（500M以内）</div>
                            <!-- <el-upload
                                action="https://jsonplaceholder.typicode.com/posts/"
                                :on-preview="handlePreview"
                                :on-remove="handleRemove"
                                :file-list="form.fileList"
                                list-type="picture">
                                <span class="but"><img :src="icon_course_name" />点击上传</span>
                                <div slot="tip" class="upok">已上传文件</div>
                            </el-upload>
                            <div class="text">支持PDF,word，图片格式，PPT，视频上传（500M以内）</div> -->
                        </div>
                    </el-form-item>

                    <el-form-item label="文件上传2：">
                        <div class="uploadFile">
                            <span class="but"><img :src="icon_course_name" />点击上传</span>
                            <div class="picList picdes">
                                <div  class="upok">已上传文件</div>
                                <ul>
                                    <li v-for="(item, index) in 4">
                                        <span>余周周的课件作品.doc</span>
                                    </li>
                                </ul>
                            </div>
                            <div class="changeUpdate">点击上传</div>
                            <div class="text">支持PDF,word，图片格式，PPT，视频上传（500M以内）</div>
                        </div>
                    </el-form-item>

                    <el-form-item>
                        <div class="uploadSubmit" @click="handleClose"><span>完成</span></div>
                    </el-form-item>
                </el-form>
            </div>
        </el-dialog>
	</div>
</template>

<script>
import icon_course_name from 'assets/images/icon/icon_course_name.png'
export default {
    name: "upload",
    props:['state'],
	components: {
		
	},
	data() {
		return {
            icon_course_name,
            loading: true,
            form: {
                name: '',
                desc: '',
                date: null,
                cat1: "1",
                cat2: "1",
                url: '',
                // fileList: [{url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}, {url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100'}]
            }
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
        },
        handleRemove(file, fileList) {
            console.log(file, fileList);
        },
        handlePreview(file) {
            console.log(file);
        }
    }
};
</script>

<style lang="scss" scoped>
.upload {
    .uploadHead {
        border-bottom: #E4E8ED 1px solid;
        margin: 0px -20px 0px;
        padding-bottom: 15px;
        h3 {
            margin-left: 20px;
            font-size: 18px;
        }
    }

    .uploadFile {
        border:1px solid rgba(220,224,230,1);
        border-radius:2px;
        padding: 10px;
        .but, .picList {
            background:rgba(245,246,248,1);
            border:1px dotted rgba(228,228,228,1);
            border-radius:2px;
            display: block;
            padding: 5px 10px;
            text-align: center;
            img {width: auto; margin-right: 10px;}
        }

        .picList {
            margin-top: 10px;
            li {
                width: 56px;
                height: 56px;
                border: #F79727 1px solid;
                display: inline-block;
                margin: 0 3px;
                img {
                    width: 56px;
                    height: 56px;
                }
            }
        }
        .picdes {
            li {
                width: 50%;
                height: auto;
                border:none;
                margin: 5px 0;
            }
        }
        .changeUpdate {
            width: 110px;
            color: #F79727;
            font-size: 14px;
            margin: 20px auto;
            background:rgba(247,151,39,.1);
            border-radius:4px;
            text-align: center;
        }

        .upok {
            text-align: center;
        }

        .text {
            text-align: center;
            color: #999;
            font-size: 12px;
        }
    }

    .uploadSubmit {
        text-align: center;
        span {
            cursor: pointer;
            background:rgba(247,151,39,1);
            border-radius:20px;
            font-size: 16px;
            color: #fff;
            padding: 10px 60px;
        }
    }
}
</style>
