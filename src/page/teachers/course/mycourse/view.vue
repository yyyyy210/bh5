<template>
	<div class="mycourseview" v-loading="loading">
		<div>
			<el-breadcrumb separator=">">
				<el-breadcrumb-item :to="{ path: '/' }">课程中心</el-breadcrumb-item>
				<el-breadcrumb-item>
					<a href="/">我的课程</a>
				</el-breadcrumb-item>
				<el-breadcrumb-item>1对1英语课程</el-breadcrumb-item>
			</el-breadcrumb>
		</div>

		<div class="view">
			<div class="des">
				<el-row>
					<el-col :span="24">
						设计图待定
					</el-col>
				</el-row>
			</div>
			<div>
				<el-row :gutter="10">
					<el-col :span="12">
						<div class="li">设计图待定</div>
					</el-col>
					<el-col :span="12">
						<div class="li">设计图待定</div>
					</el-col>
				</el-row>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "MyCourseView",
	data() {
		return {
			loading: true
		};
	},
	created() {
		let _this = this;
		setTimeout(() => {
			_this.loading = false;
		}, 1000);
	},
	methods: {}
};
</script>

<style lang="scss" scoped>
.mycourseview {
	.view {
		.des, .li {
			margin: 10px 0;
			background: #fff;
			border-radius: 5px;
			padding: 10px;
			margin-bottom: 10px;
		}
	}
}
</style>
