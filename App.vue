<template>
  <div class="app-container">

    <div class="map-wrapper">
      <Mars2dMap :url="configUrl" map-key="test" @onload="marsOnload" class="mars2d-container" />
    </div>

      <!-- 右侧组件面板 -->
      <div class="right-panel">
        <Coordinatelist :coordinates=[]></Coordinatelist>
        <sidepanel />
      </div>
    </div>
</template>


<script setup lang="ts">
import * as mars2d from "mars2d"
import Mars2dMap from "./components/mars-work/mars2d-map.vue"
// import sidepanel from "./components/mars-work/sidepanel.vue"

const configUrl = "config/config.json"

const marsOnload = (map: any) => {
  const graphicLayer = new mars2d.layer.GraphicLayer({})
  map.addLayer(graphicLayer)

  graphicLayer.on(mars2d.EventType.click, (event: any) => {
    console.log("监听layer，单击了矢量对象", event)
  })
}
</script>

<style scoped>


.app-container {
  display: flex;
}

.hidden {
  display: none; /* 隐藏元素 */
}
.map-wrapper {
  flex: 1; /* 让 map-wrapper 占据可用空间 */
  display: flex;
  justify-content: center; /* 水平居中对齐 */
  align-items: center; /* 垂直居中对齐 */
}

.right-panel {
  flex: 1; /* 让 right-panel 占据相同的空间 */
  display: flex;
  justify-content: center; /* 水平居中对齐 */
  align-items: center; /* 垂直居中对齐 */
}
</style>
