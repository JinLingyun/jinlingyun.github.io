# jinlingyun.github.io
技术博客





## app唤起功能使用

* 外部app唤起飞凡app

    * 具体的协议为`wandafeifanapp://`
    
* H5唤起内部跳转

    * 具体的协议为`wandaappfeifan://`
    
## webView使用方法

* 飞凡app加载H5页面

    * 具体的代码如下：
    
    ```javascript
    NSString *strUrl = [NSString stringWithFormat:@"wdpage://FFWebBrowserViewController?url=%@&nocache=1",[url.absoluteString urlencode]];
    
    NSURL *finalUrl = [NSURL URLWithString:strUrl];
    
    [[FFUrlSchemeManager sharedInstance] pushViewControllerWithControllerName:@"FFWebBrowserViewController" navigator:self.navigator Params:@{@"url":finalUrl}];
    ```
* 飞凡加载外部url

    * 具体的代码如下：
    
    ```javascript
    NSString* detailURL = [NSString stringWithFormat:@"http://feiyue.ffan.com/meiwen?referer=ffan_app"];
    
    NSString* strUrl = [NSString stringWithFormat:@"wdpage://FFWebBrowserViewController?url=%@&needBottomToolBar=1",[detailURL urlencode]];
    
    NSURL *url = [NSURL URLWithString:strUrl];
    
    [[FFUrlSchemeManager sharedInstance] pushViewControllerWithControllerName:@"FFWebBrowserViewController" navigator:self.navigator Params:@{@"url":url}];
    ```
    
## url Scheme的使用

* 先要将viewController注册plist中，如下图所示：

    *  ![plist](http://7xsw5d.com1.z0.glb.clouddn.com/plist.jpg?imageView2/2/w/200)
    
    
* 在plist中配置如下信息：

    * ![plistName](http://7xsw5d.com1.z0.glb.clouddn.com/plistName.png?imageView2/2/w/600)
    * `publicURL`为暴露给外部跳转用的url
    * `tagName`需要与`publicURL`中的scheme保持一致
    * `requiredParameters`为进入到该VC必传参数，由于是通过KVC直接复制，因此需要与VC中的属性名称保持一致
    * `optionalParameters`为进入到该VC的可选参数，同上
    
    
* 跳转到指定VC
 ![vc](http://7xsw5d.com1.z0.glb.clouddn.com/vc.png?imageView2/2/w/600)
pushViewController
![vcpresent](http://7xsw5d.com1.z0.glb.clouddn.com/vcpresent.png?imageView2/2/w/600)
 presentViewController
   
## 程序分支管理

* 无论子工程还是主工程之后都只有3个分支，`master`，`release`，`develop`
    
    * `master`分支用于提交appStore完成之后的版本备份，禁止直接提交代码进入master分支，master分支的代码只能从`release`合并过来
    
    * `release`分支用于定版后提交appStore的最终版本，所有需要进版提交的代码必须合并进入到`release`才可以，其他分支一律不管。
    
    * `develop`分支作为日常打包分支，每次需求提测的包都通过`develop`分支发出，所以如果哪个需求需要提测了请自行合并到develop分支。
    
    * 其他需求均可以自己创建`feature`分支，自行开发，如要提测，则必须合并到`develop`分支
    
    
* 工程代码提交
    
    * 所有工程代码提交至gerrit，经过审核后才能入库
    
    * 所有子工程通过`git submodule`方式管理，并通过gerrit控制不同权限
    
    * 主工程内的所有子工程都指向的是`head`，在gerrit内将`head`配置为`develop`，即主工程默认指向所有子工程的`develop`分支
    
    * 子工程内有修改，`子工程代码提交`
    
        * `cd 到子工程目录下`，由于主工程中，默认指向子工程的`head`，但`head`只是`develop`的一个copy，只是一个临时分支，因此需要`checkout`到需要修改的分支再修改
        
        * 执行提交之前拉取最新代码,解决冲突，并编译通过后再push，避免其他人拉取代码后编译不过
        
    * 主工程内有修改，`主工程代码提交`
    
        * 如果涉及到子工程的修改，则必须先提交子工程的修改，步骤同上
        
        * 主工程修改，在提交代码之前先执行`git submodule update`，将子工程的代码同步到`develop`的最新代码，主要是由于本地的子工程代码refs指向可能和远端不同步，如果直接提交会造成主工程内的子工程refs覆盖，导致主工程base错的子工程代码
        
        * 之后拉取主工程最新代码，解决冲突后，再提交
        
* 工程打包
    
    * 先将主工程`checkout`到指定分支，`git checkout develop`
    
    * 拉取最新代码,`git pull --rebase`
    
    * 再将所有子工程`checkout`指定分支，`git submodule foreach git checkout develop`
    
    * 所有子工程拉取最新代码，`git submodule foreach git pull --rebase`
    
    * 确保所有工程为最新代码之后即可开始打包


