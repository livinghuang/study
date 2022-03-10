# 提交 Commit

## 知識

* 建立文件 - 本地工作資料夾
* 追加文件 - 索引區
* 提交文件 - 本地庫

## 實戰

```bash
#本地工作資料夾
mkdir myweb 
cd myweb
#建立本地工作庫
git init
#追加文件與編輯 
nano index.html
#git 狀態確認
git status 
#追加文件到索引區
git add .
#提交文件到本地庫
git commit -m "first commit"
#查看提交歷史
git log
```
