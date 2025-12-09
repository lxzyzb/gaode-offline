# 离线高德地图

## 实现思路
在线高德地图通过浏览器将资源下载到本地，包括地图api文件、init文件、mapsPlugins文件、样式文件

## 下载离线地图
百度网盘链接: https://pan.baidu.com/s/12OOOAM_KIRByM68ez7Zxhw?pwd=c374 提取码: c374

## 使用步骤：

### index.html中引入js文件
```
<script src="./amap/jsapi/AMap.js"></script>
```

### 在组件内初始化
```
const layers = [new window.AMap.TileLayer({
  getTileUrl: function(x, y, z) {
    try {
      return window.location.origin + `/offlineMaps/${z}/${x}/${y}/tile.png`;  //加载离线地图资源
    } catch {
      return ''; // 返回空字符串或占位图
    }
  },
  opacity: 1,
  zIndex: 99
})]
// container为容器标签id
new window.AMap.Map('container', { // 设置地图容器id
  zoom: 12,
  resizeEnable: true,
  center: [121.880043, 29.467452],
  layers: layers
})
```
