<template>
    <el-container class="page">
        <el-header class="page-header">
            <el-row type="flex" class="header-row">
                <el-col :span=3 class="logo" :style="{width: asideWidth}">
                    logo
                </el-col>
                <el-col :span=1 @click.native="changeMenuStatus" class="menu-switch">
                    <i :class="menuStatusClass"></i>
                </el-col>
            </el-row>
        </el-header>

        <el-container class="page-body">
            <el-aside :width="asideWidth" class="menu-expanded">
                <el-menu class="meu-list"
                    text-color="#48576a"
                    active-text-color="#20a0ff"
                    background-color="#eef1f6"

                    @open="handleOpen"
                    @close="handleClose"
                    :collapse="isCollapse"
                    :collapse-transition="false"
                >
                    <el-submenu index="1">
                        <template slot="title">
                            <i class="el-icon-location"></i>
                            <span slot="title">导航一</span>
                        </template>
                        <el-menu-item-group>
                            <span slot="title">分组一</span>
                            <el-menu-item index="1-1">选项1</el-menu-item>
                            <el-menu-item index="1-2">选项2</el-menu-item>
                        </el-menu-item-group>
                        <el-menu-item-group title="分组2">
                            <el-menu-item index="1-3">选项3</el-menu-item>
                        </el-menu-item-group>
                        <el-submenu index="1-4">
                            <span slot="title">选项4</span>
                            <el-menu-item index="1-4-1">选项1</el-menu-item>
                        </el-submenu>
                    </el-submenu>
                    <el-menu-item index="2">
                        <i class="el-icon-menu"></i>
                        <span slot="title">导航二</span>
                    </el-menu-item>
                    <el-menu-item index="3" disabled>
                        <i class="el-icon-document"></i>
                        <span slot="title">导航三</span>
                    </el-menu-item>
                    <el-menu-item index="4">
                        <i class="el-icon-setting"></i>
                        <span slot="title">导航四</span>
                    </el-menu-item>
                </el-menu>
            </el-aside>
            <el-main>
                <el-steps
                    class="steps"
                    :space="200"
                    :active="active"
                    finish-status="success">
                    <el-step title="步骤 1" icon="el-icon-edit"></el-step>
                    <el-step title="步骤 2" icon="el-icon-upload"></el-step>
                    <el-step title="步骤 3" icon="el-icon-picture"></el-step>
                </el-steps>

                <el-button style="margin-top: 12px;" @click="nextStep">下一步</el-button>
            </el-main>
        </el-container>
    </el-container>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class Demo extends Vue {
    private menuData = ['配置一', '配置二', '配置三'];
    private isCollapse = false;
    private active = 0;

    // computed
    get menuStatusClass() {
        return this.isCollapse ? 'el-icon-d-arrow-right' : 'el-icon-d-arrow-left';
    }

    get asideWidth() {
        return this.isCollapse ? '65px' : '200px';
    }

    private handleOpen() {
    // console.log('menu open');
    }
    private handleClose() {
    // console.log('menu close');
    }
    private changeMenuStatus() {
        this.isCollapse = !this.isCollapse;
    }
    private nextStep() {
        if (this.active++ > 2) {
            this.active = 0;
        }
    }
}
</script>

<style lang="scss" scoped>

.page-header {
  height: 60px;
  line-height: 60px;
  background: #20a0ff;
  color: #fff;
  padding: 0;
  .logo {
    width: 200px;
    font-size: 22px;
    text-align: center;
    border-color: hsla(62, 77%, 76%, 0.3);
    border-right-width: 1px;
    border-right-style: solid;
  }
  .menu-switch {
      text-align: center;
  }
}

.page-body {
  // flex: 1;
  width: 100%;
  display: flex;
  position: absolute;
  top: 142px;
  bottom: 0;
  overflow: hidden;

  .menu-expanded {
    // width: 150px;
    height: 100%;
    background-color: #eef1f6;

    .menu-list {
      border-radius: 2px;
      list-style: none;
      position: relative;
      margin: 0;
      padding-left: 0;
      background-color: #eef1f6;
    }
  }

  .steps {
    //   text-align: left;
    // margin: 0 auto;
    justify-content: center;
  }
}
</style>
