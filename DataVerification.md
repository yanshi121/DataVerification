# DataVerification

* DataVerification是用于数据检验的工具
* 包含对多种数据的多种验证:身份证、社会信用码、时间、数字、geo数据、邮箱、电话、邮编、网络地址等
* 提供同步检验方法和异步检验方法，通过调用类来实现，异步方法在异步类中，异步类以Async结尾
* 安装DataVerification
```
pip install data-verification
```
## 主入口:data_verification

* 方法主入口，包含所有检验方法

```python
import data_verification as dv

pdv = dv.PublicDataVerification()
pdva = dv.PublicDataVerificationAsync()
gdv = dv.GeoDataValidator("", "")
gdva = dv.GeoDataValidatorAsync("", "")
```

* 所有基类方法可从相应文件导入，例如

```python
from data_verification.public.id_number import IDNumber
from data_verification.public.id_number import IDNumberAsync

idn = IDNumber()
idna = IDNumberAsync()
```
* 所有基类方法和PublicDataVerification, PublicDataVerificationAsync，GeoDataValidator, GeoDataValidatorAsync可从gather中全部获取
```python
from data_verification.gather import IDNumber
from data_verification.gather import IDNumberAsync
from data_verification.gather import PublicDataVerification
from data_verification.gather import PublicDataVerificationAsync
from data_verification.gather import LineDataValidator
from data_verification.gather import GeoDataValidator
from data_verification.gather import GeoDataValidatorAsync

idn = IDNumber()
idna = IDNumberAsync()
pdv = PublicDataVerification()
pdva = PublicDataVerificationAsync()
ldv = LineDataValidator("")
gdv = GeoDataValidator("", "")
gdva = GeoDataValidatorAsync("", "")
```
## PublicDataVerification, PublicDataVerificationAsync

```python
from data_verification import PublicDataVerification
from data_verification import PublicDataVerificationAsync

pdv = PublicDataVerification()
pdva = PublicDataVerificationAsync()
```

* 在data_verification中直接导入即可
* DataVerification包含所有的同步方法（除geo相关）
* DataVerificationAsync包含所有的异步方法（除geo相关）
* PublicDataVerification拥有异步类PublicDataVerificationAsync，其基类全部都有相对应的异步基类
* PublicDataVerification包含:
    * Regex:正则表达式相关基类
    * SCC:社会信用代码相关基类
    * Number:数字相关基类
    * Email:邮箱相关基类
    * IDNumber:身份证相关基类
    * Organization:组织机构相关基类
    * Compare:比较相关基类
    * VerifyType:类型相关基类
    * Coordinates:经纬度相关基类
    * Time:时间相关基类
    * IPAddress:网络地址相关基类
    * PhoneNumber:电话号码相关基类
    * AdminDivision:区划编号相关基类
    * Decode:字符编码相关基类
    * Postal:邮政编码相关基类
    * Empty:空值相关基类
    * Unique:唯一值相关基类
* PublicDataVerificationAsync包含:
    * RegexAsync:正则表达式相关异步基类
    * SCCAsync:社会信用代码相关异步基类
    * NumberAsync:数字相关异步基类
    * EmailAsync:邮箱相关异步基类
    * IDNumberAsync:身份证相关异步基类
    * OrganizationAsync:组织机构相关异步基类
    * CompareAsync:比较相关异步基类
    * VerifyTypeAsync:类型相关异步基类
    * CoordinatesAsync:经纬度相关异步基类
    * TimeAsync:时间相关异步基类
    * IPAddressAsync:网络地址相关异步基类
    * PhoneNumberAsync:电话号码相关异步基类
    * AdminDivisionAsync:区划编号相关异步基类
    * DecodeAsync:字符编码相关异步基类
    * PostalAsync:邮政编码相关异步基类
    * EmptyAsync:空值相关异步基类
    * UniqueAsync:唯一值相关异步基类

## GeoDataValidator, GeoDataValidatorAsync

```python
from data_verification import GeoDataValidator
from data_verification import GeoDataValidatorAsync

gdv = GeoDataValidator("", "")
gdva = GeoDataValidatorAsync("", "")
```

* 在data_verification中直接导入即可
* DataVerification包含所有geo相关的同步方法
* DataVerificationAsync包含所有geo相关的异步方法
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

