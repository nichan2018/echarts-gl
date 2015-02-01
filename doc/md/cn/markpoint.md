>ECharts-X 提供了使用 WebGL 绘制的 markPoint。并且在大部分配置项上兼容 [ECharts](http://echarts.baidu.com/doc/doc.html#SeriesMarkPoint)。

##Example - World Population
```javascript
var option = {
    title : {
        text: 'Gridded Population of the World (2000)',
        x:'center',
        y:'top',
        textStyle: {
            color: 'white'
        }
    },
    dataRange: {
        min: 0,
        max: max,
        text:['High','Low'],
        realtime: false,
        calculable : true,
        color: ['red','yellow','lightskyblue']
    },
    series: [{
        name: 'World Population',
        type: 'map3d',
        mapType: 'world',
        mapBackgroundColor: '#005f99',
        itemStyle: {
            normal: {
                borderColor: '#777'
            }
        },
        markPoint: {
            large: true,
            // Markpoint 闪烁动画
            effect: {
                show: true,
                shadowBlur: 0.4
            },
            // 异步获取的 Data
            data: populationData
        }
    }]
};
```

##MarkPoint Option

###symbol
```javascript
symbol: 'pin'
```
标注类型，详见<a href="http://echarts.baidu.com/doc/doc.html#SeriesMarkPoint">ECharts#SeriesMarkPoint</a>

###symbolSize
```javascript
symbolSize: 4
```
标注大小，要注意的是 ECharts-X 中的普通标注（`large:false`） symbolSize 并不是像素的大小，而是3D空间中的相对大小。`large:true` 时 symbolSize 对应的仍然是像素大小，而且不受缩放影响。

###large
```javascript
large: false
```
是否启用大规模标注模式

###effect
标注的呼吸动画特效，`large:true`时有效，详见<a href="http://echarts.baidu.com/doc/doc.html#SeriesMarkPoint">ECharts#SeriesMarkPoint</a>

###distance
```javascript
distance: 1
```
map3d 中 `distance` 表示标注离球体表面的距离。球体半径为 100。也可以细化到在 data 级别配置 `distance`。

###orientation
```javascript
orientation: ‘tangent’
```
标注在3D空间中的朝向，可以是标注所在表面(Surface)的切线`tangent`或者法线`normal`。只有在`large:false`的时候有效

###data
系列的标注数据, 详见<a href="http://echarts.baidu.com/doc/doc.html#SeriesMarkPoint">ECharts#SeriesMarkPoint</a>，注意 ECharts-X 中 3D 空间的标注坐标需要三个数值 x, y, z 指定。