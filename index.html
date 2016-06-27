<!DOCTYPE html>
<html lang="en-us">
  <head>
    <meta charset="UTF-8">
    <title>Jinlingyun.GitHub.io by JinLingyun</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" type="text/css" href="stylesheets/normalize.css" media="screen">
    <link href='https://fonts.googleapis.com/css?family=Open+Sans:400,700' rel='stylesheet' type='text/css'>
    <link rel="stylesheet" type="text/css" href="stylesheets/stylesheet.css" media="screen">
    <link rel="stylesheet" type="text/css" href="stylesheets/github-light.css" media="screen">
  </head>
  <body>
    <section class="page-header">
      <h1 class="project-name">Jinlingyun.GitHub.io</h1>
      <h2 class="project-tagline">技术博客</h2>
    </section>

    <section class="main-content">
      <h1>
<a id="使用cocoapods拆分子工程" class="anchor" href="#%E4%BD%BF%E7%94%A8cocoapods%E6%8B%86%E5%88%86%E5%AD%90%E5%B7%A5%E7%A8%8B" aria-hidden="true"><span aria-hidden="true" class="octicon octicon-link"></span></a>使用cocoapods拆分子工程</h1>

<ul>
<li>1.新建project，命名为FFPark，并将其拷贝到主工程中</li>
<li>2.子工程中新建pch文件，命名为FFParkPrefixHeader.pch，并将其加入系统pch配置中：
进入子工程配置文件中，Build Settings，搜索header，在precompile prefix header中设置为yes，prefix header中设置为FFPark/FFParkPrefixHeader.pch。如图：
<img src="http://7xsxl2.com2.z0.glb.clouddn.com/prefixHeader.png" alt="markdown">
</li>
<li>3.子工程中根目录新建FFPark.podspec文件，内容如下：</li>
</ul>

<div class="highlight highlight-source-js"><pre>Pod<span class="pl-k">::</span><span class="pl-smi">Spec</span>.<span class="pl-smi">new</span> <span class="pl-k">do</span> <span class="pl-k">|</span>s<span class="pl-k">|</span>
  <span class="pl-smi">s</span>.<span class="pl-c1">name</span>     <span class="pl-k">=</span> <span class="pl-s"><span class="pl-pds">'</span>FFPark<span class="pl-pds">'</span></span>
  <span class="pl-smi">s</span>.<span class="pl-c1">version</span>  <span class="pl-k">=</span> <span class="pl-s"><span class="pl-pds">'</span>1.0<span class="pl-pds">'</span></span>
  <span class="pl-smi">s</span>.<span class="pl-smi">license</span>  <span class="pl-k">=</span> <span class="pl-s"><span class="pl-pds">'</span>WD<span class="pl-pds">'</span></span>
  <span class="pl-smi">s</span>.<span class="pl-smi">author</span>   <span class="pl-k">=</span> { <span class="pl-s"><span class="pl-pds">"</span>jinlingyun<span class="pl-pds">"</span></span><span class="pl-k">=&gt;</span> <span class="pl-s"><span class="pl-pds">"</span>jinlingyun@wanda.cn<span class="pl-pds">"</span></span> }
  <span class="pl-smi">s</span>.<span class="pl-smi">requires_arc</span> <span class="pl-k">=</span> <span class="pl-c1">true</span>
  <span class="pl-smi">s</span>.<span class="pl-c1">platform</span>     <span class="pl-k">=</span> <span class="pl-k">:</span>ios, <span class="pl-s"><span class="pl-pds">'</span>7.0<span class="pl-pds">'</span></span>
  <span class="pl-smi">s</span>.<span class="pl-smi">source_files</span> <span class="pl-k">=</span> [<span class="pl-s"><span class="pl-pds">'</span>FFPark/**/*.{h,m}<span class="pl-pds">'</span></span>]
  <span class="pl-smi">s</span>.<span class="pl-smi">resources</span> <span class="pl-k">=</span> [<span class="pl-s"><span class="pl-pds">"</span>FFPark/**/*.plist<span class="pl-pds">"</span></span>,<span class="pl-s"><span class="pl-pds">"</span>FFPark/**/*.png<span class="pl-pds">"</span></span>,<span class="pl-s"><span class="pl-pds">"</span>FFPark/**/*.json<span class="pl-pds">"</span></span>,<span class="pl-s"><span class="pl-pds">"</span>FFPark/**/*.xib<span class="pl-pds">"</span></span>,<span class="pl-s"><span class="pl-pds">"</span>FFPark/**/*.storyboard<span class="pl-pds">"</span></span>]
  <span class="pl-smi">s</span>.<span class="pl-smi">prefix_header_file</span> <span class="pl-k">=</span> <span class="pl-s"><span class="pl-pds">'</span>FFPark/FFParkPrefixHeader.pch<span class="pl-pds">'</span></span>

  <span class="pl-smi">s</span>.<span class="pl-smi">frameworks</span>  <span class="pl-k">=</span> <span class="pl-s"><span class="pl-pds">'</span>QuartzCore<span class="pl-pds">'</span></span>

  <span class="pl-smi">s</span>.<span class="pl-smi">dependency</span> <span class="pl-s"><span class="pl-pds">'</span>WDWorkFlow<span class="pl-pds">'</span></span>
  <span class="pl-smi">s</span>.<span class="pl-smi">dependency</span> <span class="pl-s"><span class="pl-pds">'</span>FFFoundation<span class="pl-pds">'</span></span>
  <span class="pl-smi">s</span>.<span class="pl-smi">dependency</span> <span class="pl-s"><span class="pl-pds">'</span>WDImageTools<span class="pl-pds">'</span></span>

end</pre></div>

<ul>
<li>4.主工程中修改Podfile文件，在主target中添加：</li>
</ul>

<div class="highlight highlight-source-js"><pre>pod ‘FFPark’, <span class="pl-k">:</span><span class="pl-smi">path</span> <span class="pl-k">=&gt;</span> <span class="pl-s"><span class="pl-pds">'</span>./FFPark_src<span class="pl-pds">'</span></span></pre></div>

<p>同时添加target :FFPark，如下：</p>

<div class="highlight highlight-source-js"><pre>target <span class="pl-k">:</span>FFPark <span class="pl-k">do</span>
    xcodeproj <span class="pl-s"><span class="pl-pds">'</span>FFPark_src/FFPark<span class="pl-pds">'</span></span>
    link_with <span class="pl-s"><span class="pl-pds">"</span>FFPark<span class="pl-pds">"</span></span>
    pod <span class="pl-s"><span class="pl-pds">'</span>WDWorkFlow<span class="pl-pds">'</span></span>, <span class="pl-k">:</span><span class="pl-smi">path</span> <span class="pl-k">=&gt;</span> <span class="pl-s"><span class="pl-pds">'</span>./WDWorkFlow_src<span class="pl-pds">'</span></span>
    pod <span class="pl-s"><span class="pl-pds">'</span>WDImageTools<span class="pl-pds">'</span></span>, <span class="pl-k">:</span><span class="pl-smi">path</span> <span class="pl-k">=&gt;</span> <span class="pl-s"><span class="pl-pds">'</span>./WDImageTools<span class="pl-pds">'</span></span>
    pod <span class="pl-s"><span class="pl-pds">'</span>FFFoundation<span class="pl-pds">'</span></span>, <span class="pl-k">:</span><span class="pl-smi">path</span> <span class="pl-k">=&gt;</span> <span class="pl-s"><span class="pl-pds">'</span>./FFFoundation<span class="pl-pds">'</span></span>
end</pre></div>

<ul>
<li>5.运行update_pods命令：./update_pods
该命令内容如下：</li>
</ul>

<div class="highlight highlight-source-shell"><pre>ps -ef <span class="pl-k">|</span> grep  <span class="pl-s"><span class="pl-pds">"</span>/Applications/Xcode.app/Contents/MacOS/Xcode<span class="pl-pds">"</span></span> <span class="pl-k">|</span> grep -v grep <span class="pl-k">|</span> awk <span class="pl-s"><span class="pl-pds">'</span>{print $2}<span class="pl-pds">'</span></span> <span class="pl-k">|</span> xargs <span class="pl-c1">kill</span> -9

pod update --no-repo-update

ls <span class="pl-k">|</span> grep <span class="pl-s"><span class="pl-pds">"</span>.xcworkspace<span class="pl-pds">"</span></span> <span class="pl-k">|</span> xargs open</pre></div>

<p>运行之后，可以在Pods子工程中看到FFPark文件夹，该文件夹实际上是子工程FFPark的文件镜像或替身</p>

<ul>
<li>6.编译子工程</li>
</ul>

<p>子工程引用子工程的代码，直接import进来即可，主工程也可以引用子工程的代码
但要子工程引用主工程的代码，则不行，但有两种方法，1使用桥，2使用运行时</p>

<p>1使用桥，如下示例</p>

<p>要拆分的子工程中的代码：</p>

<div class="highlight highlight-source-objc"><pre>RTLbsAnnotation *tapAnnotation = [[RTLbsAnnotation <span class="pl-c1">alloc</span>] <span class="pl-c1">initWithMapPoint:</span><span class="pl-c1">CGPointMake</span>([manager.fixMemberInfo.fixXCoordinate <span class="pl-c1">floatValue</span>], [manager.fixMemberInfo.fixYCoordinate <span class="pl-c1">floatValue</span>]) <span class="pl-c1">title:</span><span class="pl-s"><span class="pl-pds">@"</span><span class="pl-pds">"</span></span> <span class="pl-c1">iconImage:</span>[UIImage <span class="pl-c1">imageNamed:</span><span class="pl-s"><span class="pl-pds">@"</span>car_carposition_icon<span class="pl-pds">"</span></span>] <span class="pl-c1">floorID:</span>floorIndex];</pre></div>

<p>而RTLbsAnnotation.h是在主工程中定义的， #import “RTLbsAnnotation.h"提示找不到RTLbsAnnotation.h这个文件。此时需要在拆分的子工程中添加头文件如 FFParkInterBridge.h，在该头文件中定义：</p>

<div class="highlight highlight-source-objc"><pre>interface RTLbsAnnotation : NSObject
- (<span class="pl-k">id</span>) initWithMapPoint: (<span class="pl-c1">CGPoint</span>) mapPoint title: (<span class="pl-c1">NSString</span> *)title iconImage:(UIImage *) iconImage floorID:(<span class="pl-c1">NSString</span>*)floor;
end</pre></div>

<p>相当于在主工程和子工程中搭了一座桥，此时注释掉 #import “RTLbsAnnotation.h”，则可以编译通过，运行时会自动找到主工程中的代码来运行</p>

<p>2使用运行时，如下示例（该方法不推荐，没有经过严格测试，只是说明思路）：</p>

<p>要拆分的子工程中的代码：</p>

<div class="highlight highlight-source-objc"><pre>-(<span class="pl-k">void</span>)openWebViewWithURL:(<span class="pl-c1">NSString</span>*) url urlSort:(<span class="pl-c1">NSString</span>*)urlsort{
    [FFAdvertisementSkipNewViewController <span class="pl-c1">nav2NextListViewController:</span><span class="pl-v">self</span>.controller <span class="pl-c1">urlSort:</span>model.urlSort <span class="pl-c1">urlContent:</span>model.urlContent];
}</pre></div>

<p>而FFAdvertisementSkipNewViewController是在主工程中定义的，则使用如下代码，也可保证编译及运行通过：</p>

<div class="highlight highlight-source-objc"><pre>-(<span class="pl-k">void</span>)openWebViewWithURL:(<span class="pl-c1">NSString</span>*) url urlSort:(<span class="pl-c1">NSString</span>*)urlsort{
    <span class="pl-k">id</span> vc =<span class="pl-c1">NSClassFromString</span>(<span class="pl-s"><span class="pl-pds">@"</span>FFAdvertisementSkipNewViewController<span class="pl-pds">"</span></span>);

    <span class="pl-k">SEL</span> selector = <span class="pl-c1">NSSelectorFromString</span>(<span class="pl-s"><span class="pl-pds">@"</span>nav2NextListViewController:urlSort:urlContent:<span class="pl-pds">"</span></span>);

    [<span class="pl-v">self</span> <span class="pl-c1">performMethodWithTarget:</span>vc <span class="pl-c1">selector:</span>selector <span class="pl-c1">withObjects:</span>@[<span class="pl-v">self</span>,urlsort,url]];
}

- (<span class="pl-k">void</span>)performMethodWithTarget:(<span class="pl-k">id</span>)target selector:(<span class="pl-k">SEL</span>)selector withObjects:(<span class="pl-c1">NSArray</span> *)objects
{
    <span class="pl-c">// 方法签名(方法的描述)</span>
    <span class="pl-c1">NSMethodSignature</span> *signature = [target <span class="pl-c1">methodSignatureForSelector:</span>selector];
    <span class="pl-k">if</span> (signature == <span class="pl-c1">nil</span>) {
        <span class="pl-k">return</span>;
        <span class="pl-c">//可以抛出异常也可以不操作。</span>
    }

    <span class="pl-c">// NSInvocation : 利用一个NSInvocation对象包装一次方法调用（方法调用者、方法名、方法参数、方法返回值）</span>
    <span class="pl-c1">NSInvocation</span> *invocation = [<span class="pl-c1">NSInvocation</span> <span class="pl-c1">invocationWithMethodSignature:</span>signature];
    invocation.<span class="pl-smi">target</span> = target;
    invocation.<span class="pl-smi">selector</span> = selector;

    <span class="pl-c">// 设置参数</span>
    <span class="pl-k">NSInteger</span> paramsCount = signature.<span class="pl-smi">numberOfArguments</span> - <span class="pl-c1">2</span>; <span class="pl-c">// 除self、_cmd以外的参数个数</span>
    <span class="pl-k">if</span>(paramsCount!=objects.<span class="pl-smi">count</span>)
    {
        <span class="pl-k">return</span>;
    }
    <span class="pl-k">for</span> (<span class="pl-k">NSInteger</span> i = <span class="pl-c1">0</span>; i &lt; paramsCount; i++) {
        <span class="pl-k">id</span> object = objects[i];
        <span class="pl-k">if</span> ([object <span class="pl-c1">isKindOfClass:</span>[<span class="pl-c1">NSNull</span> <span class="pl-c1">class</span>]]) <span class="pl-k">continue</span>;
        [invocation <span class="pl-c1">setArgument:</span>&amp;object <span class="pl-c1">atIndex:</span>i + <span class="pl-c1">2</span>];
    }

    <span class="pl-c">// 调用方法</span>
    [invocation <span class="pl-c1">invoke</span>];
}</pre></div>

<p>7.待拆分子工程编译通过后，删除主工程中该模块的代码，再编译主工程</p>

      <footer class="site-footer">

        <span class="site-footer-credits">This page was generated by <a href="https://pages.github.com">GitHub Pages</a> using the <a href="https://github.com/jasonlong/cayman-theme">Cayman theme</a> by <a href="https://twitter.com/jasonlong">Jason Long</a>.</span>
      </footer>

    </section>

  
  </body>
</html>
