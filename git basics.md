# Git 概念

# Git文件状态

仓库中的文件可能存在于这三种状态：

- Untracked files → 文件未被跟踪；
- Changes to be committed → 文件已暂存，这是下次提交的内容；
- Changes not staged for commit → 已跟踪文件的内容发生了变化，但还没有放到暂存区。

通过git add的文件会加入暂存区，之后git commit会将暂存区的所有文件提交更新。 

working directory -> index/staging area -> local repo -> remote repo

![Staging](img/staging.jpg)

# Git对象和目录

在Git系统中，每个Git对象都通过哈希值来代表这个对象。哈希值是通过SHA1算法计算出来的，长度为40个字符（40-digit）。

commit, tree, blob, tag四种object

![commit tree blob三种对象的关系](img/commit tree blob.jpg)

![git对象结构的关系图](img/git object.jpg)

所有的内容都是环环相扣的，我们通过HEAD找到一个当前分支，然后通过当前分支的引用找到最新的commit，然后通过commit可以找到整个对象关系模型： 
![对象关系模型](img/object hierachy.jpg)


## .git目录

git会将所有的文件，目录，提交等转化为git对象，压缩存储在.git文件夹当中。

- HEAD: 这个文件包含了一个branch的引用，通过这个文件Git可以得到下一次commit的parent
- ORIG_HEAD: HEAD指针的前一个状态
- config: git repo的配置文件
- description: repo的描述信息，主要给gitweb等git托管系统使用
- index: 这个文件就是我们前面提到的暂存区（stage），是一个二进制文件
- COMMIT_EDITMSG: 保存最新的commit message，Git系统不会用到这个文件，只是给用户一个参考
- ./hooks: 这个目录存放一些shell脚本，可以设置特定的git命令后触发相应的脚本；在搭建gitweb系统或其git托管系统会经常用到hook script
- ./info: 包含仓库的一些信息
- ./logs: 保存所有更新的引用记录
- ./objects: 所有的Git对象都会存放在这个目录中，对象的SHA1哈希值的前两位是文件夹名称，后38位作为对象文件名
- ./refs: 这个目录一般包括三个子文件夹，heads、remotes和tags，heads中的文件标识了项目中的各个分支指向的当前commit

## 参考

https://zhuanlan.zhihu.com/p/44741777
