<template>
  <div>
  <el-menu class="el-menu-demo" mode="horizontal">
    <el-menu-item index="1"><a href="https://github.com/ipfs/js-ipfs" target="_blank"><img class="logo" src="https://camo.githubusercontent.com/44d46e125f11fe293dde1e6c92760b1ad6253132/68747470733a2f2f697066732e696f2f697066732f516d566b37737272776168584c4e6d634459767955454a7074796f78706e646e52613537594a31314c346a5632362f697066732e6a732e706e67"/></a></el-menu-item>

    <el-menu-item index="5" @click="openNodeInfo"> <el-button :plain="true" size="small" type="info">info</el-button> </el-menu-item>
    <el-menu-item index="5">{{status}}</el-menu-item>
    <el-menu-item index="6">Connected Peers: {{node.peers.length}}</el-menu-item>
    <el-menu-item index="7"></el-menu-item>
    <el-menu-item index="8">
          <el-button v-if="status === 'stopped'" type="primary" size="small" @click="startNode">Start</el-button>
          <el-button v-if="status != 'stopped'" type="danger" size="small" @click="stopNode">Stop</el-button>
          <el-button v-if="status === 'starting'" type="simple" :loading="true" size="small">Starting</el-button>
    </el-menu-item>
  </el-menu>
  </div>
</template>

<script>
import {mapActions, mapState} from 'vuex'
export default {
  computed: {
    ...mapState({
      status: state => state.ipfs.status,
      node: state => state.ipfs
    })
  },
  methods: {
    ...mapActions([
      'startNode',
      'stopNode',
      'openNodeInfo'
    ])
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  .logo {
    max-width: 100px
  }
  .el-menu {
    background: none;
    border-bottom: 1px solid #e9eced
  }
  .el-menu--horizontal .el-menu-item {
    background: none!important;
    border: none!important;
  }
</style>
