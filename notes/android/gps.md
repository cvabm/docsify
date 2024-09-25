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
 
 ## 原始gps信息
 GNRMC/GPGGA/PSTMDRGPS比较  

GNRMC:多系统支持：GNRMC语句支持多种全球导航卫星系统（GNSS），包括GPS、GLONASS、Galileo和北斗等。这意味着在偏远地区，即使某个系统的信号较弱，其他系统的信号可能仍然可用，从而提高了定位的可靠性和准确性。  
GPGGA:综合信息：GNRMC不仅提供了经纬度信息，还包括速度、航向和日期等信息，这对于导航和定位应用非常有用。  
PSTMDRGPS:与常见的NMEA语句如GNRMC和GPGGA相比，PSTMDRGPS提供了更详细的定位质量信息，适用于需要高精度定位和质量监控的应用场景  

选择：  
如果你的应用需要支持多种导航卫星系统，并且需要速度、航向和日期信息，建议使用GNRMC。  
如果你的应用需要详细的定位质量信息和高度信息，并且仅使用GPS系统，建议使用GPGGA。  
用于需要高精度定位和质量监控的应用场景，用PSTMDRGPS。  

## 精确度
```

小数点后1位：精度约为10公里。
小数点后2位：精度约为1公里。
小数点后3位：精度约为100米。
小数点后4位：精度约为10米。
小数点后5位：精度约为1米。
小数点后6位：精度约为0.1米（10厘米）。
小数点后7位：精度约为0.01米（1厘米）。
小数点后8位：精度约为0.001米（1毫米）。
```