# 基础数据校验

## 区划编码检验:AdminDivision,AdminDivisionAsync

* 根据国标（GB/T 2260-2007）验证各级编码

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.admin_division import AdminDivision

ad = AdminDivision()
```

* 使用方法完全一致，只是引用不同，也可使用异步方法，将引用转为异步即可

### province_division_2007

* 根据国标（GB/T 2260-2007）验证省级区划编码
* 携带一个参数
    * code:编码

```python
from data_verification.admin_division import AdminDivision

ad = AdminDivision()
ad.province_division_2007("code")
```

### city_division_2007

* 根据国标（GB/T 2260-2007）验证市级区划编码
* 携带一个参数
    * code:编码

```python
from data_verification.admin_division import AdminDivision

ad = AdminDivision()
ad.city_division_2007("code")
```

### county_division_2007

* 根据国标（GB/T 2260-2007）验证县级区划编码
* 携带一个参数
    * code:编码

```python
from data_verification.admin_division import AdminDivision

ad = AdminDivision()
ad.county_division_2007("code")
```

### division_2007

* 根据国标（GB/T 2260-2007）验证省市县级区划编码
* 携带一个参数
    * code:编码

```python
from data_verification.admin_division import AdminDivision

ad = AdminDivision()
ad.division_2007("code")
```

## 比较检验:Compare,CompareAsync

* 根据国标（GB/T 2260-2007）验证各级编码
* 携带一个参数
    * code:编码

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.compare import Compare

c = Compare()
```

* 使用方法完全一致，只是引用不同，也可使用异步方法，将引用转为异步即可

### verify_compare

* 对两个数据进行比较验证
* 携带三个参数
    * value1:数据1
    * value2:数据2
    * pattern:验证模式，默认为0，0:是否小于，1:是否大于，2:是否等于，3:是否小于等于，4:是否大于等于，5:是否不等于

```python
from data_verification.compare import Compare

c = Compare()
c.verify_compare(1, 2, 0)
```

### verify_length

* 验证数据长度
* 携带三个参数
    * value:被验证数据
    * length:数据长度
    * pattern:验证模式，默认为0，0:是否小于，1:是否大于，2:是否等于，3:是否小于等于，4:是否大于等于，5:是否不等于

```python
from data_verification.compare import Compare

c = Compare()
c.verify_length("as", 2, 0)
```

### compare_hashes

* 比较数据对象与对应哈希值是否相同
* 携带三个参数
    * data: 被验证数据对象
    * hash_value: 比对哈希值
    * algorithm: 使用的哈希算法名称，默认为sha256，支持；sha1，sha224，sha256，sha384，sha512，sha3_224，sha3_256，
      sha3_384，sha3_512，shake_128，shake_256，blake2b，blake2s，md5

```python
from data_verification.compare import Compare

c = Compare()
c.compare_hashes("as", "")
```

## 经纬度检验:Coordinates,CoordinatesAsync

* 根据国标（GB/T 2260-2007）验证各级编码

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.coordinates import Coordinates

c = Coordinates()
```

### verify_latitude

* 纬度范围验证
* 携带三个参数
    * latitude:被验证纬度
    * start_latitude_scope:起始纬度，大于-90
    * end_latitude_scope:结束纬度，小于90

```python
from data_verification.coordinates import Coordinates

c = Coordinates()
c.verify_latitude(50, 40, 80)
```

### verify_longitude

* 经度范围验证
* 携带三个参数
    * longitude:被验证经度
    * start_longitude_scope:起始经度，大于-180
    * end_longitude_scope:结束经度，小于180

```python
from data_verification.coordinates import Coordinates

c = Coordinates()
c.verify_longitude(50, 40, 80)
```

### verify_coordinates

* 经纬度范围验证
* 携带六个参数
    * latitude:被验证纬度
    * start_latitude_scope:起始纬度，大于-90
    * end_latitude_scope:结束纬度，小于90
    * longitude:被验证经度
    * start_longitude_scope:起始经度，大于-180
    * end_longitude_scope:结束经度，小于180

```python
from data_verification.coordinates import Coordinates

c = Coordinates()
c.verify_coordinates(50, 40, 80, 50, 40, 80)
```

### verify_china_latitude

* 中国纬度验证
* 携带一个参数
    * latitude:纬度

```python
from data_verification.coordinates import Coordinates

c = Coordinates()
c.verify_china_latitude(50)
```

### verify_china_longitude

* 中国经度验证
* 携带一个参数
    * longitude:经度

```python
from data_verification.coordinates import Coordinates

c = Coordinates()
c.verify_china_longitude(50)
```

### verify_china_coordinates

* 中国经度验证
* 携带两个参数
    * latitude:纬度
    * longitude:经度

```python
from data_verification.coordinates import Coordinates

c = Coordinates()
c.verify_china_coordinates(50, 50)
```

### verify_global_latitude

* 全球纬度验证
* 携带一个参数
    * latitude:纬度

```python
from data_verification.coordinates import Coordinates

c = Coordinates()
c.verify_global_latitude(50)
```

### verify_global_longitude

* 全球经度验证
* 携带一个参数
    * longitude:经度

```python
from data_verification.coordinates import Coordinates

c = Coordinates()
c.verify_global_longitude(50)
```

### verify_global_coordinates

* 全球经纬度验证
* 携带两个参数
    * latitude:纬度
    * longitude:经度

```python
from data_verification.coordinates import Coordinates

c = Coordinates()
c.verify_global_coordinates(50, 50)
```

## 字符编码检验:Decode,DecodeAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.decode import Decode

d = Decode()
```

### decode

* 验证字符编码格式
* 携带两个参数
    * data: 被验证的数据
    * encoding: 编码类型

```python
from data_verification.decode import Decode

d = Decode()
d.decode("asd", 'utf-8')
```

## 值域检验:Domain,DomainAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.domain import Domain

d = Domain()
```

### enum_domain_check

* 检查给定值是否在预定义的有效值列表中
* 携带两个参数
    * value: 要检查的值
    * valid_values: 有效值的列表

```python
from data_verification.domain import Domain

d = Domain()
d.enum_domain_check("asd", 'utf-8')
```

### encoded_domain_check

* 检查给定值是否符合指定的编码规则
* 携带两个参数
    * value: 要检查的值
    * encoding_rule: 编码规则函数，返回布尔值

```python
from data_verification.domain import Domain


def check(c):
    return c.isdigit()


d = Domain()
d.encoded_domain_check("a1d", check)
```

### dictionary_domain_check

* 检查给定值是否存在于字典中，并且其对应的值满足指定条件
* 携带三个参数
    * value: 要检查的值（通常是键）
    * dictionary: 键值对集合
    * condition: 条件函数，接收字典中的值作为参数，返回布尔值。(可选)

```python
from data_verification.domain import Domain

d = Domain()
d.dictionary_domain_check("asd", {"asd": 2, "as": 2})
```

### dictionary_enum_domain_check

* 检查给定值是否在字典表中，并且其对应的值属于预定义的有效值列表
* 携带两个参数
    * value: 要检查的值（通常是键）
    * enum_dict: 键值对集合，其中值是一个包含有效枚举值的列表

```python
from data_verification.domain import Domain

d = Domain()
d.dictionary_enum_domain_check("asd", {"asd": 2, "as": 2})
```

## 邮箱检验:Email,EmailAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.email import Email

e = Email()
```

### verify_email_format

* 验证邮箱是否符合规则
* 携带一个参数
    * email: 被验证邮箱

```python
from data_verification.email import Email

e = Email()
e.verify_email_format("aaa@aa.com")
```

## 空值检验:Empty,EmptyAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.empty import Empty

e = Empty()
```

### is_empty

* 检查给定值是否为空
* 携带一个参数
    * value: 要检查的值

```python
from data_verification.empty import Empty

e = Empty()
e.is_empty("")
```

### is_not_empty

* 检查给定值是否非空
* 携带一个参数
    * value: 要检查的值

```python
from data_verification.empty import Empty

e = Empty()
e.is_not_empty("")
```

## 身份证检验:IDNumber,IDNumberAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.id_number import IDNumber

idn = IDNumber()
```

### verify_id_number

* 对身份证号进行验证
* 携带三个参数
    * vid_number: 身份证号
    * factors: 权重因子
    * check_codes: 校验码映射表

```python
from data_verification.id_number import IDNumber

idn = IDNumber()
idn.verify_id_number("512345678941253678")
```

## 网络地址检验:IPAddress,IPAddressAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.ip_address import IPAddress

ipa = IPAddress()
```

### verify_mac_address

* 对Mac地址进行验证
* 携带一个参数
    * mac_address: 被验证的Mac地址

```python
from data_verification.ip_address import IPAddress

ipa = IPAddress()
ipa.verify_mac_address("")
```

### verify_ipv4

* 对IPv4地址进行验证
* 携带一个参数
    * ip_address: 被验证的IPv4地址

```python
from data_verification.ip_address import IPAddress

ipa = IPAddress()
ipa.verify_ipv4("")
```

### verify_ipv6

* 对IPv6地址进行验证
* 携带一个参数
    * ip_address: 被验证的IPv6地址

```python
from data_verification.ip_address import IPAddress

ipa = IPAddress()
ipa.verify_ipv6("")
```

### verify_ip_address

* 对IPv4或IPv6地址进行验证
* 携带一个参数
    * ip_address: 被验证的IPv4或IPv6地址

```python
from data_verification.ip_address import IPAddress

ipa = IPAddress()
ipa.verify_ip_address("")
```

## 数字检验:Number,NumberAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.number import Number

n = Number()
```

### number_range

* 验证数是否在某个区间，前后闭区间
* 携带四个参数
    * value: 被验证数
    * min_value: 区间小值
    * max_value: 区间大值
    * pattern: 区间判断类型默认为0，0：前闭后闭，1：前闭后开，2：前开后闭，3：前开后开

```python
from data_verification.number import Number

n = Number()
n.number_range(5, 1, 6)
```

### check_precision

* 检查数值是否符合指定的精度要求
* 携带四个参数
    * value: 要检查的数值字符串或数字
    * min_value: 允许的最小值，默认为None表示无下限
    * max_value: 允许的最大值，默认为None表示无上限
    * decimal_places: 小数点后允许的最大位数，默认为2

```python
from data_verification.number import Number

n = Number()
n.check_precision(5.21)
```

## 组织机构检验:Organization,OrganizationAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.organization import Organization

o = Organization()
```

### verify_organization_code

* 验证组织机构代码
* 携带两个参数
    * code: 组织机构代码
    * weights: 权重数组

```python
from data_verification.organization import Organization

o = Organization()
o.verify_organization_code("5445sd545")
```

## 电话号码检验:PhoneNumber,PhoneNumberAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.phone_number import PhoneNumber

pn = PhoneNumber()
```

### verify_mobile_number

* 对移动手机号进行验证
* 携带一个参数
    * phone_number: 被验证手机号

```python
from data_verification.phone_number import PhoneNumber

pn = PhoneNumber()
pn.verify_mobile_number("12345678941")
```

### verify_fixed_line_number

* 对固定电话号进行验证
* 携带一个参数
    * phone_number: 被验证电话号

```python
from data_verification.phone_number import PhoneNumber

pn = PhoneNumber()
pn.verify_fixed_line_number("2255-554145264")
```

### verify_phone_number

* 对移动手机号或固定电话号进行验证
* 携带一个参数
    * phone_number: 被验证移动手机号或固定电话号

```python
from data_verification.phone_number import PhoneNumber

pn = PhoneNumber()
pn.verify_phone_number("12345678941")
```

## 邮政编码检验:Postal,PostalAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.postal import Postal

p = Postal()
```

### postal_code

* 验证邮政编码是否正确
* 携带两个参数
    * postal_code: 被验证编码
    * country_code: 地区默认CN，目前支持CN-中国，US-美国，GB-英国，DE-德国，FR-法国，AU-澳大利亚，JP-日报，IN-印度，RU-俄罗斯，
      IT-意大利，ES-西班牙，NL-荷兰，CH-瑞士，BR-巴西，CA-加拿大，AR-阿根廷，AT-奥地利，BE-比利时，CL-智利，CO-哥伦比亚，DK-丹麦，
      FI-荷兰，GR-希腊，HU-匈牙利，ID-印度尼西亚，IE-爱尔兰，IL-以色列，KR-韩国，LU-卢森堡，MY-马来西亚，MX-墨西哥，NZ-新西兰，NO-挪威，
      PL-波兰，PT-葡萄牙，RO-罗马尼亚，SG-新加坡，ZA-南非，SE-瑞典，TH-泰国，TR-土耳其，UA-乌克兰，VN-越南

```python
from data_verification.postal import Postal

p = Postal()
p.postal_code("552255", 'CN')
```

## 自定义正则检验:Regex,RegexAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.regex import Regex

r = Regex()
```

### regex

* 基于正则表达式验证值的内容
* 携带两个参数
    * value: 被验证值
    * pattern: 正则表达式

```python
from data_verification.regex import Regex

r = Regex()
r.regex("552255", 'CN')
```

## 社会信用代码检验:SCC,SCCAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.scc import SCC

scc = SCC()
```

### verify_uscc

* 统一社会信用代码校验
* 携带三个参数
    * code: 统一社会信用代码
    * weights: 权重数组
    * check_code_map: 校验码映射表

```python
from data_verification.scc import SCC

scc = SCC()
scc.verify_uscc("")
```

### verify_cscc

* 企业社会信用代码校验
* 携带三个参数
    * code: 企业社会信用代码
    * weights: 权重数组
    * check_code_map: 校验码映射表

```python
from data_verification.scc import SCC

scc = SCC()
scc.verify_cscc("")
```

## 时间检验:Time,TimeAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.time import Time

t = Time()
```

### time_range

* 验证时间戳或带格式时间是否在某个区间
* 携带五个参数
    * time: 被验证时间
    * start_time: 起始时间
    * end_time: 结束时间
    * time_format: 时间格式
    * pattern: 区间判断类型，0：前闭后闭，1：前闭后开，2：前开后闭，3：前开后开

```python
from data_verification.time import Time

t = Time()
t.time_range("", '', '')
```

### datetime_range

* 验证带有格式的时间是否在某个区间
* 携带五个参数
    * time: 被验证时间
    * start_time: 起始时间
    * end_time: 结束时间
    * time_format: 时间格式
    * pattern: 区间判断类型，0：前闭后闭，1：前闭后开，2：前开后闭，3：前开后开

```python
from data_verification.time import Time

t = Time()
t.datetime_range("", '', '')
```

### timestamp_range

* 验证时间戳是否在某个区间
* 携带四个参数
    * timestamp: 被验证的时间戳
    * start_timestamp: 起始时间戳
    * end_timestamp: 结束时间戳
    * pattern: 区间判断类型，0：前闭后闭，1：前闭后开，2：前开后闭，3：前开后开

```python
from data_verification.time import Time

t = Time()
t.timestamp_range("", '', '')
```

### verify_date

* 对日期进行验证
* 携带两个参数
    * date_string: 被验证的日期
    * date_format: 日期格式化规则

```python
from data_verification.time import Time

t = Time()
t.verify_date("")
```

### verify_timestamp

* 对时间戳进行验证
* 携带一个参数
    * timestamp: 被验证的时间戳

```python
from data_verification.time import Time

t = Time()
t.verify_timestamp("")
```

### check_timeliness

* 检查给定的时间戳是否符合及时性要求
* 携带三个参数
    * timestamp_str: 时间戳字符串
    * date_format: 时间戳的格式，默认为"%Y-%m-%d %H:%M:%S"
    * timeliness_threshold_minutes: 数据被认为是及时的最大分钟数，默认为60分钟

```python
from data_verification.time import Time

t = Time()
t.check_timeliness("")
```

## 类型检验:VerifyType,VerifyTypeAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.verify_type import VerifyType

vt = VerifyType()
```

### is_bytes

* 验证是否是二进制数据
* 携带一个参数
    * value: 被验证数据

```python
from data_verification.verify_type import VerifyType

vt = VerifyType()
vt.is_bytes("")
```

### is_bool

* 验证是否是布尔值
* 携带一个参数
    * value: 被验证数据

```python
from data_verification.verify_type import VerifyType

vt = VerifyType()
vt.is_bool("")
```

### is_str

* 验证是否是字符串
* 携带一个参数
    * value: 被验证数据

```python
from data_verification.verify_type import VerifyType

vt = VerifyType()
vt.is_str("")
```

### is_float

* 验证是否是浮点数
* 携带一个参数
    * value: 被验证数据

```python
from data_verification.verify_type import VerifyType

vt = VerifyType()
vt.is_float("")
```

### is_int

* 验证是否是整数
* 携带一个参数
    * value: 被验证数据

```python
from data_verification.verify_type import VerifyType

vt = VerifyType()
vt.is_int("")
```

## 唯一值检验:Unique,UniqueAsync

```python
from data_verification import PublicDataVerification

pdv = PublicDataVerification()
```

或者

```python
from data_verification.unique import Unique

u = Unique()
```

### is_unique

* 检查列表中的元素是否全部唯一
* 携带一个参数
    * lst: 要检查的列表

```python
from data_verification.unique import Unique

u = Unique()
u.is_unique("")
```