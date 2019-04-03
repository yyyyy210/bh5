<template>
	<div class="classedit" v-loading="loading">
        <el-dialog :visible.sync="state" width="70%" :before-close="handleClose">
			<span slot="title" class="title">
				<h3>课件编辑</h3>
			</span>
			<div class="group">
				classedit
			</div>
        </el-dialog>
	</div>
</template>

<script>

export default {
    name: "classedit",
    props:['state'],
	components: {
		
	},
	data() {
		return {
            loading: true,
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
.classedit {
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
}
</style>
