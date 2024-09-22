- [展示wgs84位置](#wgs84)

# wgs84
- 第一种方式
`https://www.openstreetmap.org/`  
输入`39.946025,116.397051` 点击搜索，鼠标需悬停在搜索结果的地址或经纬度上，地图上才显示红色marker图标
- 第二种方式(失效)
打开谷歌地球，直接搜经纬度，但是还是会自动切换为gcj02坐标系，可以切换语言或地区后试试

# 原生
- 重置gps服务  
LocationManager towerLocationManager = (LocationManager) getSystemService(Context.LOCATION_SERVICE);
towerLocationManager.sendExtraCommand("gps", "force_xtra_injection", bundle); //快速定位command
towerLocationManager.sendExtraCommand("gps", "force_time_injection", bundle);
towerLocationManager.sendExtraCommand("gps", "delete_aiding_data", bundle); //冷启动


- https://github.com/android/location-samples.git 必须google sevice
- https://github.com/mendhak/gpslogger 
- https://github.com/barbeau/gpstest
 