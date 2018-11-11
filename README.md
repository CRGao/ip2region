ip2region - 最自由的ip地址查詢庫，ip到地區的映射庫，提供Binary,B樹和純內存三種查詢算法，媽媽再也不用擔心我的ip地址定位。

##將該庫打包成 PHP composer 版本

### 1. 99.9%準確率，定時更新：

數據聚合了一些知名ip到地名查詢提供商的數據，這些是他們官方的的準確率，經測試著實比純真啥的準確多了。 <br />
每次聚合一下數據需要1-2天，會不定時更新。

### 2. 標準化的數據格式：

每條ip數據段都固定了格式：_城市Id|國家|區域|省份|城市|ISP_

只有中國的數據精確到了城市，其他國家只能定位到國家，後前的選項全部是0，已經包含了全部你能查到的大大小小的國家。
（請忽略前面的城市Id，個人項目需求）

### 3. 體積小：

生成的數據庫文件ip2region.db只有1.5M（1.2版本前是3.5M）

### 4. composer 安裝：
```php
composer require crgao/ip2region
```

```php
$ip2region = new Ip2Region();

$ip = '101.96.11.3';

#可拿來驗證IP格式
$ip = Ip2Region::safeIp2long($ip);

#btreeSearch
$info = $ip2region->btreeSearch($ip);
print_r($info);

#binarySearch
$info = $ip2region->binarySearch($ip);
print_r($info);

#memorySearch
$info = $ip2region->memorySearch($ip);
print_r($info);

```

