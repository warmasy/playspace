# git

## 初始化设置

1. 配置用户名

   ```bash
   git config --global user.name "用户名" 
   ```

   - --global 表示全局参数
   - --system 系统配置，对所有用户生效

2. 配置邮箱

   ```bash
   git config --global user.email "xxx@qq.com" 
   ```

3. 保存用户名和密码，不用每次都输入

   ```bash
   git config --global credential.helper store
   ```

   - 设置 Git 的凭据管理器（credential helper）为 store 模式，此模式下会保存 HTTP/HTTPS 请求时的用户名和密码。在首次进行需要身份验证的操作（如 git push 或 git pull）时，Git 会提示输入用户名和密码，并将这些凭据保存到 ~/.git-credentials 文件中，之后需要身份验证时，Git 会自动使用保存的凭据，而不再提示输入。

4. 查看git配置的信息

   ```bash
   git config --global --list
   ```

**注：** 命令1，2只需配置一次就行

## 创建目录

```bash
git init # 在当前文件夹下创建目录(会生成一个.git隐藏目录)
git init my-repo # 在my-repo下创建仓库(会生成一个my-reop目录，并在my-repo下生成.git隐藏目录)
```

## 克隆仓库

~~~bash
git clone https://github.com/warmasy/autonote.git
~~~

## git的工作区域和文件的状态

### 工作区域

git的本地数据管理分为3个区域，分别是**工作区**，**暂存区**和**本地仓库**。

- 工作区：.git所在的目录。

- 暂存区：.git/index，用于保存即将提交到git仓库的修改内容。就相当于一个中间区域，用于临时存放即将提交的修改内容。

- 本地仓库：.git/object，git存储代码和版本信息的主要位置。

当修改好工作区的文件之后，需要将他们添加到暂存区，然后再将暂存区的修改内容提交到本地仓库中。

### 文件的状态

git中的文件也存在几种状态，分别是未跟踪，未修改，已修改和已暂存

- 未跟踪：我们创建的还没有被git管理的文件。
- 未修改：我们已经被git管理起来，但是文件的内容没有发生变化，还没有被修改过
- 已修改：我们已经修改过的文件，但是还没有添加到暂存区里面。
- 已暂存：我们修改后并且已经添加到了暂存区内的文件

![image-20250727150519117](https://oss-20241110-pic.oss-cn-hangzhou.aliyuncs.com/%E6%96%87%E4%BB%B6-250727/image-20250727150519117.png)

## 添加和提交文件

1. 查看仓库状态

   ~~~bash
   git status
   ~~~

2. 将文件提交到暂存区

   ~~~bash
   git add file1.txt # 将file1.txt添加到暂存区
   ~~~

   ```bash
   git add . # 将当前目录所有文件添加到暂存区
   ```

   ~~~bash
   git -rm --cached <file> # 取消暂存某文件
   ~~~

3. 提交到仓库中

   只会提交暂存区中的文件到仓库中

   ~~~bash
   git commit -m "提交说明"
   ~~~

4. 查看提交记录

   ~~~bash
   git log
   
   ~~~

5. 撤销之前修改的一些内容，或者回退到之前的某一个版本,并且保存工作区和暂存区的修改内容

   ```
   git reset
   ```

   ```
   git reset --soft
   git reset --hard
   git reset --mixed
   ```

   - soft：回退到之前的某一个版本,并且保存工作区和暂存区的修改内容

   - hard：表示回退到某一个版本，并且丢弃工作区和暂存区的所有修改内容

   - mixed：介于soft和hard这两个参数之间，它表示回退到某一个版本，并且只保存工作区的修改内容而丢弃暂存区的修改内容

6. .将文件同时从工作区和暂存区删掉

   ```
   git rm file1.txt
   git rm --catch file1.txt # 把文件从暂存区删除，但保留在当前工作区中。
   ```

   删除之后提交一下，保存到版本库中

## .gitignore文件

.gitignore文件的作用是可以让我们忽略掉一些不应该被加入到版本库中的文件

应该忽略那些文件？

1. 系统或者软件自动生成的文件
2. 编译产生的中间文件和结果文件
3. 运行时生成的日志文件、缓存文件、临时文件
4. 涉及身份、密码、口令、密钥等敏感信息文件

一个.gitignore文件示例

```bash
*.log # 忽略所有以log结尾的文件
temp/ # 忽略temp文件夹，注意：文件夹的格式是以斜线结尾的，这样才能正确的忽略文件夹。
```

注意：在版本库中的文件不会被忽略，

.gitignore文件的匹配规则：

1.从上到下逐行匹配，每一行表示一个忽略模式

2.空行或者以#开头的行会被git忽略。一般空行用于可读性的分割，#一般用作注释

3.使用标准的Blob模式匹配，例如：*：统配任意个字符，？：比配单个字符，**：匹配任意的中间目录

## 远程仓库推送与拉取

### 把本地仓库和别名为origin的远程仓库关联起来

```
git push -u origin main
```

### git pull

git pull（拉取）：把远程仓库的修改拉取到本地仓库

```bash
git pull
```

### git push

git push（推送）：把本地仓库的修改推送给远程仓库

```bash
git push
```

## 常用基本操作

1. 克隆项目


   ```bash
   git clone
   ```

2. 查看当前仓库所对应的远程仓库的别名和地址


   ```bash
   git remote -v
   ```

3. 把本地仓库和别名为origin的远程仓库关联起来


   ```bash
   git push -u origin main
   ```

4. 将文件添加到暂存区,等待后续的提交操作


   ```bash
   git add <文件名>
   ```

5. 将当前文件夹下的文件全部添加到暂存区里面


   ```bash
   git add . 
   ```

6. 提交文件到本地仓库(只会提交暂存区中的文件，不会提交工作区的其他文件)


   ```bash
   git commit -m "提交信息"
   ```

7. 把暂存区的文件提交到远程仓库


   ```
   git push
   ```

8. git pull（拉取）：把远程仓库的修改拉取到本地仓库


   ```bash
   git pull
   ```







































