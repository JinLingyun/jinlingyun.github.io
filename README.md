#使用cocoapods拆分子工程

* 1.新建project，命名为FFPark，并将其拷贝到主工程中
* 2.子工程中新建pch文件，命名为FFParkPrefixHeader.pch，并将其加入系统pch配置中：
进入子工程配置文件中，Build Settings，搜索header，在precompile prefix header中设置为yes，prefix header中设置为FFPark/FFParkPrefixHeader.pch。如图：
![markdown](http://7xsxl2.com2.z0.glb.clouddn.com/prefixHeader.png)
* 3.子工程中根目录新建FFPark.podspec文件，内容如下：
```javascript
Pod::Spec.new do |s|
  s.name     = 'FFPark'
  s.version  = '1.0'
  s.license  = 'WD'
  s.author   = { "jinlingyun"=> "jinlingyun@wanda.cn" }
  s.requires_arc = true
  s.platform     = :ios, '7.0'
  s.source_files = ['FFPark/**/*.{h,m}']
  s.resources = ["FFPark/**/*.plist","FFPark/**/*.png","FFPark/**/*.json","FFPark/**/*.xib","FFPark/**/*.storyboard"]
  s.prefix_header_file = 'FFPark/FFParkPrefixHeader.pch'

  s.frameworks  = 'QuartzCore'

  s.dependency 'WDWorkFlow'
  s.dependency 'FFFoundation'
  s.dependency 'WDImageTools'

end
```
* 4.主工程中修改Podfile文件，在主target中添加：
```javascript
pod ‘FFPark’, :path => './FFPark_src'
```
同时添加target :FFPark，如下：
```javascript
target :FFPark do
    xcodeproj 'FFPark_src/FFPark'
    link_with "FFPark"
    pod 'WDWorkFlow', :path => './WDWorkFlow_src'
    pod 'WDImageTools', :path => './WDImageTools'
    pod 'FFFoundation', :path => './FFFoundation'
end
```
* 5.运行update_pods命令：./update_pods
该命令内容如下：
```bash
ps -ef | grep  "/Applications/Xcode.app/Contents/MacOS/Xcode" | grep -v grep | awk '{print $2}' | xargs kill -9

pod update --no-repo-update

ls | grep ".xcworkspace" | xargs open
```
运行之后，可以在Pods子工程中看到FFPark文件夹，该文件夹实际上是子工程FFPark的文件镜像或替身

* 6.编译子工程

子工程引用子工程的代码，直接import进来即可，主工程也可以引用子工程的代码
但要子工程引用主工程的代码，则不行，但有两种方法，1使用桥，2使用运行时

1使用桥，如下示例

要拆分的子工程中的代码：
```objectivec
RTLbsAnnotation *tapAnnotation = [[RTLbsAnnotation alloc] initWithMapPoint:CGPointMake([manager.fixMemberInfo.fixXCoordinate floatValue], [manager.fixMemberInfo.fixYCoordinate floatValue]) title:@"" iconImage:[UIImage imageNamed:@"car_carposition_icon"] floorID:floorIndex];
```
而RTLbsAnnotation.h是在主工程中定义的， #import “RTLbsAnnotation.h"提示找不到RTLbsAnnotation.h这个文件。此时需要在拆分的子工程中添加头文件如 FFParkInterBridge.h，在该头文件中定义：
```objectivec
interface RTLbsAnnotation : NSObject
- (id) initWithMapPoint: (CGPoint) mapPoint title: (NSString *)title iconImage:(UIImage *) iconImage floorID:(NSString*)floor;
end
```
相当于在主工程和子工程中搭了一座桥，此时注释掉 #import “RTLbsAnnotation.h”，则可以编译通过，运行时会自动找到主工程中的代码来运行

2使用运行时，如下示例（该方法不推荐，没有经过严格测试，只是说明思路）：

要拆分的子工程中的代码：
```objectivec
-(void)openWebViewWithURL:(NSString*) url urlSort:(NSString*)urlsort{
    [FFAdvertisementSkipNewViewController nav2NextListViewController:self.controller urlSort:model.urlSort urlContent:model.urlContent];
}
```
而FFAdvertisementSkipNewViewController是在主工程中定义的，则使用如下代码，也可保证编译及运行通过：
```objectivec
-(void)openWebViewWithURL:(NSString*) url urlSort:(NSString*)urlsort{
    id vc =NSClassFromString(@"FFAdvertisementSkipNewViewController");

    SEL selector = NSSelectorFromString(@"nav2NextListViewController:urlSort:urlContent:");

    [self performMethodWithTarget:vc selector:selector withObjects:@[self,urlsort,url]];
}

- (void)performMethodWithTarget:(id)target selector:(SEL)selector withObjects:(NSArray *)objects
{
    // 方法签名(方法的描述)
    NSMethodSignature *signature = [target methodSignatureForSelector:selector];
    if (signature == nil) {
        return;
        //可以抛出异常也可以不操作。
    }

    // NSInvocation : 利用一个NSInvocation对象包装一次方法调用（方法调用者、方法名、方法参数、方法返回值）
    NSInvocation *invocation = [NSInvocation invocationWithMethodSignature:signature];
    invocation.target = target;
    invocation.selector = selector;

    // 设置参数
    NSInteger paramsCount = signature.numberOfArguments - 2; // 除self、_cmd以外的参数个数
    if(paramsCount!=objects.count)
    {
        return;
    }
    for (NSInteger i = 0; i < paramsCount; i++) {
        id object = objects[i];
        if ([object isKindOfClass:[NSNull class]]) continue;
        [invocation setArgument:&object atIndex:i + 2];
    }

    // 调用方法
    [invocation invoke];
}
```
7.待拆分子工程编译通过后，删除主工程中该模块的代码，再编译主工程


