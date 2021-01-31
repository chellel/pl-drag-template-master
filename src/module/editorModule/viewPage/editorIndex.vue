<template>
  <div class="page-editor">
    <!--组件&页面&模板-->
    <div class="editor-page-edit-wrapper">
      <componentLibs/>
    </div>
    <!--页面编辑区域-->
    <div class="editor-main">
      <control-bar :scale.sync="projectData.scale" @save="saveEditor"/>
      <editor-pan/>
    </div>
    <!--属性编辑区域-->
    <div class="el-attr-edit-wrapper">
		<editor-drawer ref="editorDrawer"></editor-drawer>
    </div>
  </div>
</template>

<script>
  import { Component, Vue, Watch } from 'vue-property-decorator'
  import componentLibs from '../components/componentLibs'
  import editorPan from '../components/editorPan'
  import editorDrawer from '../components/editorDrawer'
  import controlBar from '../components/control-bar'
  import {namespace} from 'vuex-class'
  const editorModule = namespace('editorModule')
  @Component({components: { componentLibs, editorPan, controlBar, editorDrawer }, name: 'editorIndex'})
  // 可视化页面编辑器入口
  export default class editorIndex extends Vue {
    @editorModule.State('projectData') projectData
    @editorModule.State('activeElementUUID') activeElementUUID
    
    
    // 保存模板
    saveEditor () {
      console.log(this.projectData)
    }

    // 监听当前选中项，如果存在就打开右边侧滑框进行配置
    @Watch('activeElementUUID')
    activeElementUUIDChange (val) {
      // 开打弹窗
      if (val) {
        this.$refs.editorDrawer.show()
      } else {
        this.$refs.editorDrawer.hide()
      }
    }
  }
</script>

<style lang="less" scoped>
  .page-editor {
    display: flex;
    min-width: 1280px;
    height: 100%;
    position: relative;
    .editor-page-edit-wrapper {
      width: 210px;
      padding: 0 1px;
    }
    .editor-main {
      flex: 1;
      position: relative;
    }
    .el-attr-edit-wrapper {
      height: 100%;
      position: relative;
      background-color: #f0f0f0;
      width: 405px;
      padding: 0;
     
    }
  }
</style>
