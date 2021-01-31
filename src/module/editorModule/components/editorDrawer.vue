<template>
	<div>
		<div class="editorDrawer" :style="{ width: visible ? editorDrawerWidth + 'px' : '0' }" ref="editorDrawer">
			<el-tabs v-model="activeAttr" stretch v-if="visible">
				<el-tab-pane label="属性" name="a">
					属性-----根据自己的实际组件自己配置
				</el-tab-pane>
				<el-tab-pane label="样式" name="b">
					样式-----根据自己的实际组件自己配置
				</el-tab-pane>
			</el-tabs>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'editorDrawer',
		props: {

		},
		data() {
			return {
				visible: false, // 控制编辑栏弹窗
				editorDrawerWidth: 405, // 编辑栏的宽度
				activeAttr: 'a'
			}
		},
		methods: {
			show() {
				this.visible = true;
			},
			hide() {
				this.visible = false;
			}

		},
		created() {

		}
	}
</script>

<style lang="less">
	.editorDrawer {
		height: 100%;
		overflow: hidden;
		transition: width .3s;
		position: absolute;
		top: 0;
		right: 0;
		background-color: white;
	}
</style>
