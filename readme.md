#### node_modules 中的版本

**问题：**Package.json中的版本，由于老项目使用cnpm安装，没有出现锁定版本，导致如果cnpm升级或者npm不能安装，包容易错

**解答：**1. 可以使用 npm i -g cnpm@7.0.0 安装指定的cnpm版本；2.可以按照跑起来的项目的node_modules 锁定Package.json中的版本