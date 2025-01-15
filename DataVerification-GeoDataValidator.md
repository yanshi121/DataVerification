# geo数据检验

## GeoDataValidator

* GeoDataValidator拥有异步类GeoDataValidatorAsync，但是其基类没有相对应的异步基类
* GeoDataValidator包含:
    * LineDataValidator-矢量线数据位置合理性验证
    * PolygonDataValidator-矢量面数据位置合理性验证
    * PointDataValidator-矢量点数据位置合理性验证
    * LineTopologyValidator-线拓扑规则合理性验证
    * PolygonTopologyValidator-面拓扑规则合理性验证
    * PointTopologyValidator-点拓扑规则合理性验证
* GeoDataValidator以及GeoDataValidatorAsync初始化包含三个参数
    * file_path: 地理数据shp文件路径
    * validator_type: 验证器类型，如 'point_data'-矢量点数据位置合理性, 'line_data'-矢量线数据位置合理性,
      'polygon_data'-矢量面数据位置合理性, 'point_topology'-点拓扑规则合理性, 'line_topology'-线拓扑规则合理性,
      'polygon_topology'-面拓扑规则合理性
    * boundary_file_path: 边界多边形shp文件地址（可选）
* GeoDataValidator包含两个方法
    * check_validity: 检查地理数据位置合理性和拓扑规则
    * check_specific_validity: 检查特定地理要素的位置合理性和拓扑规则

### GeoDataValidator.check_validity

* 检查地理数据位置合理性和拓扑规则
* 携带一个参数
    * kwargs: 传递给具体检查方法的关键字参数

```python
from data_verification import GeoDataValidator

gdv = GeoDataValidator("", "")
gdv.check_validity()
```

### GeoDataValidator.check_specific_validity

* 检查特定地理要素的位置合理性和拓扑规则
* 携带两参数
    * index: 要检查的要素索引
    * kwargs: 传递给具体检查方法的关键字参数

```python
from data_verification import GeoDataValidator

gdv = GeoDataValidator("", "")
gdv.check_validity()
```

## LineDataValidator

* 矢量线数据位置合理性验证
* LineDataValidator初始化包含两个参数
    * line_file_path: 线数据shp文件地址
    * boundary_file_path: 边界多边形shp文件地址（可选）

### LineDataValidator.check_line_data_validity

* 检查矢量线数据的位置合理性
* 不携带参数

```python
from data_verification.geo import LineDataValidator

ldv = LineDataValidator("")
ldv.check_line_data_validity()
```

## PolygonDataValidator

* 矢量面数据位置合理性验证
* PolygonDataValidator初始化包含两个参数
    * line_file_path: 面数据shp文件地址
    * polygon_file_path: 边界多边形shp文件地址（可选）

### PolygonDataValidator.check_polygon_data_validity

* 检查矢量面数据的位置合理性
* 携带一个参数
    * allow_holes: 是否允许多边形内存在孔洞，默认为 False

```python
from data_verification.geo import PolygonDataValidator

pdv = PolygonDataValidator("")
pdv.check_polygon_data_validity()
```

## PointDataValidator

* 矢量点数据位置合理性验证
* PointDataValidator初始化包含两个参数
    * point_file_path: 点数据shp文件地址
    * boundary_file_path: 边界多边形shp文件地址（可选）

### PointDataValidator.check_point_data_validity

* 检查矢量面数据的位置合理性
* 携带三个参数
    * check_within_boundaries: 是否检查点是否位于边界内，默认为 True
    * line_file_path: 用于检查点到线距离的线数据文件路径（可选）
    * max_distance: 允许的最大距离，单位与坐标系一致，默认为 0.0 表示必须重合

```python
from data_verification.geo import PointDataValidator

pdv = PointDataValidator("")
pdv.check_point_data_validity()
```

## LineTopologyValidator

* 线拓扑规则合理性验证
* LineTopologyValidator初始化包含两个参数
    * line_file_path: 线数据shp文件地址
    * boundary_file_path: 边界多边形shp文件地址（可选）

### LineTopologyValidator.check_line_topology_validity

* 检查矢量线数据的拓扑规则合理性
* 携带一个参数
    * check_within_boundaries: 是否检查线是否位于边界内，默认为 True

```python
from data_verification.geo import LineTopologyValidator

ltv = LineTopologyValidator("")
ltv.check_line_topology_validity()
```

### LineTopologyValidator.check_specific_line

* 检查某条特定线的拓扑规则合理性
* 携带一个参数
    * index: 要检查的线的索引

```python
from data_verification.geo import LineTopologyValidator

ltv = LineTopologyValidator("")
ltv.check_specific_line(0)
```

## PolygonTopologyValidator

* 面拓扑规则合理性验证
* PolygonTopologyValidator初始化包含两个参数
    * polygon_file_path: 面数据shp文件地址
    * boundary_file_path: 边界多边形shp文件地址（可选）

### PolygonTopologyValidator.check_polygon_topology_validity

* 检查矢量面数据的拓扑规则合理性
* 携带两个参数
    * allow_holes: 是否允许多边形内存在孔洞，默认为 False
    * check_within_boundaries: 是否检查多边形是否位于边界内，默认为 True

```python
from data_verification.geo import PolygonTopologyValidator

ptv = PolygonTopologyValidator("")
ptv.check_polygon_topology_validity()
```

### PolygonTopologyValidator.check_specific_polygon

* 检查某个多边形的拓扑规则合理性
* 携带两个参数
    * index: 要检查的多边形的索引
    * allow_holes: 是否允许该多边形内存在孔洞，默认为 False

```python
from data_verification.geo import PolygonTopologyValidator

ptv = PolygonTopologyValidator("")
ptv.check_specific_polygon(0)
```

## PointTopologyValidator

* 点拓扑规则合理性验证
* PointTopologyValidator初始化包含三个参数
    * point_file_path: 点数据shp文件地址
    * line_file_path: 线数据shp文件地址
    * boundary_file_path: 边界多边形shp文件地址（可选）

### PointTopologyValidator.check_point_topology_validity

* 检查矢量点数据的拓扑规则合理性
* 携带两个参数
    * check_within_boundaries: 是否检查点是否位于边界内，默认为 True
    * check_proximity_to_lines: 是否检查点到线的距离，默认为 True
    * max_distance: 允许的最大距离，单位与坐标系统一致，默认为 0.0 表示必须重合

```python
from data_verification.geo import PointTopologyValidator

ptv = PointTopologyValidator("")
ptv.check_point_topology_validity()
```

### PointTopologyValidator.check_specific_point

* 检查某个特定点的拓扑规则合理性
* 携带四个参数
    * index: 要检查的点的索引
    * check_within_boundaries: 是否检查点是否位于边界内，默认为 True
    * check_proximity_to_lines: 是否检查点到线的距离，默认为 True
    * max_distance: 允许的最大距离，单位与坐标系统一致，默认为 0.0 表示必须重合

```python
from data_verification.geo import PointTopologyValidator

ptv = PointTopologyValidator("")
ptv.check_specific_point(0)
```