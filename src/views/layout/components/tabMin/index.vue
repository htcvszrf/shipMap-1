<template>
  <div class="min-warp-view"
       :style="{width, height, top, right}">
    <ul class="min-warp-view-box">
      <li class="min-warp-view-item" v-for="(item, index) in minimizeWindows" :key="index" @click="revivification(index,item.routeName)">
          <span>{{item.title}}</span>
          <span>
            <svg-icon class="setting"  icon-class="revivification"/>
          </span>
      </li>
    </ul>
  </div>
</template>
<script>
import {
  mapGetters
} from 'vuex'
export default {
  name: 'minWindows',
  props: {
    width: String,
    height: String,
    top: String,
    right: String
  },
  computed: {
    ...mapGetters([
      'minimizeWindows'
    ])
  },
  data() {
    return {
    }
  },
  methods: {
    revivification(index, name) {
      const curIndex = this.minimizeWindows.findIndex(item => item.routeName === name)
      if (curIndex !== -1) {
        this.minimizeWindows[curIndex].zoomAction()
        this.minimizeWindows.splice(curIndex, 1)
      }
    }
  },
  mounted() {
  }
}
</script>
<style>
.min-warp-view ul,
.min-warp-view li{
  padding: 0;
  margin: 0;
  list-style: none;
}
.min-warp-view .min-warp-view-box {
  display: flex;
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
}
.min-warp-view {
  position: fixed;
  z-index: 1;
  bottom: 10px;
  left: 10px;
  color: #fff;
  font-size: 12px;
  letter-spacing: 0;
}
.min-warp-view .min-warp-view-box .min-warp-view-item {
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.5);
  line-height: 32px;
  width: 148px;
  padding: 0 10px;
  display: flex;
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  -webkit-justify-content: space-between;
  -moz-justify-content: space-between;
  -ms-justify-content: space-between;
  -o-justify-content: space-between;
  justify-content: space-between;
  border-radius: 2px;
  background: rgba(24,24,24,0.80);
  margin-right: 6px;
}
.min-warp-view .min-warp-view-box .min-warp-view-item .setting{
  margin-top: 10px;
  width: 13px;
  height: 13px;
  color: #fff;
}
</style>
