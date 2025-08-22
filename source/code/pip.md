# pip

## 基本用法

### pip版本与升级

   ```
   pip --version # 查看pip版本
   ```

   ```
   pip install --upgrade pip # 升级pip
   ```

   ```
   pip config list -v # 查看pip配置
   ```

### python包的安装卸载升级

1. 安装

   ```
   pip install Sphinx
   ```

   安装对应版本

   ```
   pip install Sphinx==8.3.0
   ```

2. 卸载

   ```
   pip uninstall Sphinx
   ```

3. 升级

   ```
   pip install --upgrade pip
   ```
   ```
   升级包到当前最新的版本，可以使用-U 或者 --upgrade
   pip install Sphinx --upgrade
   pip install -U Sphinx
   ```

### 包管理

1. 查看包详情

   ```
   pip show netkiller-logging
   ```

2. 列出已经安装的包

	```
	pip list
	```

3. 查看需要升级的包

   ```
   pip list -o
   ```
   
4. 查看所有包版本

   ```
   pip freeze
   ```

5. 把当前所有包的名称及版本输出到某一文件

   ```
   pip freeze > requirements.txt
   ```

6. 批量安装库

	```
	pip install -r requirements.txt
	```
	
7. 验证已安装的包是否有兼容依赖问题

	```
	pip check package-name
	```

### 使用镜像源安装

1. 例

   ```
   pip install sphinx -i https://pypi.tuna.tsinghua.edu.cn/simple 
   ```

2. 切换 pip 镜像

   ```
   pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple # 永久性切换
   ```

### 开源镜像站

1. ```python
   https://pypi.tuna.tsinghua.edu.cn/simple # 清华大学开源软件镜像站
   ```

2. ```python
   https://mirrors.aliyun.com/pypi/simple/ # 阿里云开源镜像站
   ```

3. ```python
   https://mirrors.ustc.edu.cn/pypi/simple/ # 中国科学技术大学开源软件镜像
   ```

4. ```python
   https://repo.huaweicloud.com/repository/pypi/simple/ # 华为云开源镜像站
   ```

5. ```python
   https://mirrors.cloud.tencent.com/pypi/simple/ # 腾讯软件源
   ```
   
6. ```python
   https://mirrors.163.com/pypi/simple/ # 网易开源镜像站
   ```

## 常用操作

```
pip install sphinx -i https://pypi.tuna.tsinghua.edu.cn/simple 
```

