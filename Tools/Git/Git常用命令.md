



## 配置

### 配置账号信息
```bash
git config -e [--global] # 命令行界面直接编辑Git配置文件, [可选]

git config --global user.name 'zewail' # 修改全局名字
git config --global user.email 'chanzewail@gmail.com' # 修改全局邮箱地址

git config --list # 查看配置信息
```
### 配置自动换行
建议统一使用LF（UNIX）自动换行
```bash
git config --global core.autocrlf input # 自动将换行符转换为LF
```

### 配置密钥
#### 创建密钥

如果你已经创建过 ssh key，可以通过以下命令查询 ssh key 列表
```bash
ls -al ~/.ssh
```
否则就创建一个
```bash
ssh-keygen -t rsa -b 4096 -C "chanzewail@gmail.com"
# ssh-keygen -t rsa -b 4096 -C "chanzewail@gmail.com" -f zewail_rsa # 通过-f参数来指定密钥文件名称
```
创建的密钥默认名称为 `id_rsa`私钥和 `id_rsa.pub`公钥, 如果修改了密钥默认名称, 需要加入到ssh_agent中

```bash
ssh-add -K ~/.ssh/zewail_rsa
```
#### 添加到github

进入`Settings`->`SSH and GPG keys`->`New SSH key`, `title`自定义，将复制的公钥填入`Key`中，然后`Add SSH key.`完成
```bash
 pbcopy < ~/.ssh/id_rsa.pub # 复制公钥信息到剪切板
```

#### 测试
```bash
ssh -T git@github.com # 测试是否成功  
```
