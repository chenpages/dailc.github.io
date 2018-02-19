# 阿里巴巴钉钉团队面试

## 最前面的电话了解（严格来说不属于面试）

自我介绍了了下，了解了下自己两年多经验，有hybrid框架以及项目驱动型移动框架

然后问了下svn协作提交等（说了下发布目录，tag等等）

然后大概介绍了下自己的移动前端框架以及hybrid的思路

然后被问了一个：数组如何深复制-稍微提了下es5的slice，concat，es6的解构等
（json.stringif，join，split等忘提了）

然后大概说了下风险是：经验不够？（这点可能是沟通失误，后来说了下是2-3年间，估计问题不大）

电话了解后就走了内推

## 一面（电话面试-@贵重）

标准的自我介绍：

- 15年江大毕业到现在，刚开始Android，一两个月后就转前端，到现在两年以上的前端开发经验

- 主要成果：一个是hybrid模式的混合开发框架，一个是项目驱动型移动前端框架

    - 介绍了下hybrid模式大概是迭代了3个版本，从原生的window到scheme再到js-core方式
    
    - API规范方面也是从原始的交互到有一定规范再到尽量优雅的规范
    
    - 提到了参考钉钉
    
- 发展历程：最开始5+选型，到发现5+不符合要求，于是自己公司研发了适合自己公司的hybrid
    
然后从hybrid模式框架问起：大概是3.x和2.x的优化（回答主要是规范和文档方面）

然后问了下大致的亮点：回答-有一个多平台支撑功能，可以支持h5，原始环境下多种情景

然后问了下框架sdk是否可定制：第一次回答是有组件化这个概念，项目自己去拓展自己的组件API，完善功能。
不过好像不是想要这个结果，是问框架打包能否定制化

回答是：没有实践过（目前的框架sdk是固定的），不过大概可以说下思路是需要配置文件打包，发送到服务端，自动打包时打包特定代码

问了下后续的优化：回答是离线资源更新
（现在全是走在线的，离线可以通过一个配置文件，然后每次映射在线资源，如果离线有，并且版本合适就用离线，
离线版本不合适，就更新离线等等），以及权限认证，数据埋点等等


又问了下移动前端框架的，大概回答了下，没用vue，react等，是最原始的加一堆的工具类，组件，方便开发，以及加了一个简单的gulp工作流方便打包合并。

被问到了：为什么不用Vue组件化之类的。

回答：尝试推动过 vue，不过失败了，阐述了下失败原因是被领导认为过于复杂
（演示时用了webpack+自动化+vue-mvvm等一系列流程，导致被认为和以前的开发模式相差过大，所以拒绝，
着重说了下自己当时经验不够，导致没有突出重点，没有突出优点-可以突出优点是性能优化，代码复用等等，
反而让人觉得和以前模式区别过大，被拒绝）

被问了下有没有成功推动的case：

ejs系列，从h5+转型到ejs
（因为h5+更适合产生各种不同的项目，而我司更类似于一个标准产品，在产品上修改迭代），
然后经过1.x，2.x，3.x的迭代。
特别是2.x到3.x（是通过API规格不足，交互方式有损耗，调用麻烦，代码复用低等原因）

然后被问了下：框架大概都做了什么

回答：常用工具类（身份证，常用方法extend，loadjs），组件（轮播，下拉刷新，日历等），以及上层的业务封装（代理用户token等）

被问了下css布局，如何适应各种屏幕：回答是rem+@media，不过没有和框架组合，更多的都是技术方案与建议

又问了下有没有优化的实践：说了下出了优化方案-类似于军规，以及以前有一个框架给他们用webpack出了一个优化版本，用来解决前端资源打包合并问题。

最后感觉面试官是想听到：线上项目的优化实践。。。

被问了下异步加载js：async，defer，以及脚本动态加载（常用的），也顺便提了下xhr等可能方案

然后问了下脚本动态加载如何判断完成：回答是有一个onreadystate状态（大概，具体名字忘了），通过不同状态判断不同阶段，完成了就回调，
顺便提了下css的加载在某些浏览器下有问题，所以一般css都是默认为加载完毕，避免判断失误，无法回调

被问了下cookie和session：没按标准答案来，说了下自己理解，cookie主要是前端和服务端交互
（中间提了下cookie会默认带上，跨域不带，所以有静态资源的多域名优化-http1.1），
然后session是服务端存具体信息的东西，提了下sessionid这个概念。
登陆后，服务端给页面写入session ID，然后页面自动带上cookie

本问了下：cookie什么时候不会被脚本读取（跨域情况以及httponly-放xss攻击）

最后被问了一个经典问题：浏览器输入URL发生了什么

先从浏览器进程说起，主控进程控制开启http，然后进行dns查询-先本机，然后路由（这个掉了），网络，
然后找到IP后三次握手建立联系（提了下底层其实有封装成帧，物理层传输等概念），
然后实质的http请求，获取body后解析（这块掉了http各大头部，如缓存等，缓存是可以提下的，下次注意），
浏览器拿到后，用内核解析（其实可以提下每一个tab都有浏览器内核），提了下里面有词法分析等等，
（说到这时这里又补充了下，前面还有下载时如果检测到资源单独开下载线程下载，包括每个域名的资源限制6个以及多域名优化等等）
然后就是经典的解析：dom，css规则，rending树，绘制渲染，然后dom加载完毕，js线程接管。
（其实可以加上css绘制时有复合层和普通层这个概念，这样就可以顺便提到3d加速了）

然后问了下vue，react等，回答是现在在看vue源码，后续还会看react源码，稍微说了下vue的理解：

- 从mvvm机制（数据。数据有依赖，解析dom时会生成watcher，每一个依赖都会有watcher，
然后数据observe，变动时更新依赖队列-其实可以提下dom主要监听input变化，然后更改数据等），
说到对象数组递归监听（包括数组实现的特殊方式，需要劫持原型，以及dep和watcher的绑定）（提了下后续会继续跟进）

问了下对钉钉产品的了解：

开发过钉钉应用，但是没有怎么实践过钉钉产品，因为公司有自己的产品。
（被问了下如何通信，回答是自己的微消息-虽然用了第三方大蚂蚁的方案）

然后问了下有没有什么要问的。

1. 技术栈以及去了做什么：回答是react+node+原生jsbridge，但没有专门的框架维护人员，而是可能会安排不同人员进行优化，补充。
然后说明了下主要是按业务条线划分，可能是不同阶段有不同任务，并不限制react和node的使用，完全看业务来
（估计是因为人员能力都不错的原因），
然后过去后应该在某一个业务线，整个团队40多人左右，并不限制技术，所以可以发挥，追求产品极致

2. 这次发挥，有什么建议：总体回答应该感觉答的还不错，然后说了下平时可能主要是框架，业务以及项目经验方面不一定很足
（这里又提了下与时间划分有关，关系不大），应该是想表明后续钉钉团队是按业务条线色

最后提了下一面完后会有一个初步的级别划分等等

以及最后让将提到的技术方案，文档发过去（技术文档发了链接，内部方案截了一张图做代表）

整体感觉一面层次偏高（并不关注某个基础API），应该是leader型或专家型面的

## 二面（电话面试-@佩玉[p9]）

很意外，在9.30时突然接到一个电话，然后直接就开始面试流程了

首先，仍然是自我介绍，大概分为几个部分：（重点，一定要加上业余学习JS原理，vue源码等，要给boss合适的提纲）

- 介绍自己15年毕业，到现在3年左右经验，2年多的前端

- 主要成果，一个是hybrid模式混合开发框架（用来解决混合开发问题，减少原生人员的投入，复用大量的只会jsp的那种初级前端成员），
一个是契合这个公司业务的移动前端框架（符合这个公司业务，尽量简单，比较契合简单业务常见的项目型开发）

- 介绍了自己的发展历程，成长速度是第一年慢，第二年快，原因是第二年开始规划人生，利用大量的工作之余，业余时间，
学习，成长，开源，写组件，看源码

- 补充（后续补充的），业余时间基本安排满了，用来学习技术，看源码，写开源

然后问了下写了什么组件：

- 基于公司的hybrid模式混合开发框架抽取出来了，自己负责前端，Android，前端，重新架构，结合一个朋友帮忙ios，
重新梳理了一遍，加深了理解

- H5下拉刷新组件，比较受欢迎，700多star了，自己在这个项目成长了不少，
包括文档，merge，解决issue，（尝试单元测试，es6语法，gulp+rollup等）

- 其它，如调用某个canvas截图时，会习惯性的开源，其它也一样，基本上有新的技术学习或研究都会开源

然后被问了下hybrid模式框架：

- API规范部分，参考钉钉进行规划，尽量优雅

- 原生交互层次，JSBridge进行交互

- 组件API部分，按功能划分组件，而且框架有框架核心组件，项目可以继承某个类定义自己的自定义组件，方便拓展

- 还有类似于config白名单，权限等边角功能

- 还做了一个多平台支撑，如ui.alert除了支持native还支持h5，便于复用代码，提升效率

被问了下有哪些API

- 按组件划分模块，如UI里面是alert,toast这些，device里是设备号，震动等，runtime里如版本号获取，还有其它二维码扫码等等

- 前端调用js即可使用原生功能

被问了下交互原理

- 核心是JSBridge，说了下三个版本的迭代，第一个版本，直接在window里注入，第二个版本采用iframe+src调用urlscheme解析，
第三个版本（现在）利用JSCore，iOS中注入wkwebviewjsbridge对象方便前端调用，Android中利用chrome的prompt，避免了注入

- 然后说了下解析规则大概是：模块+方法+参数+回调端口，然后对于原生方法执行完毕后就会回调，前端调用对应的回调

- 又说了下长期回调和短期的划分，短期是alert这种，调用完毕后立即回调，前端也销毁回调方法，长期是按钮点击事件这种，
调用后，符合某个条件，就会触发回调，然后前端就会触发回调

然后被问了cookie

- 浏览器和服务端交互，譬如登陆后，后台会生成一个session，里面包含用户信息，然后会有一个sessionID，
将session ID写入页面作为cookie，然后以后页面再访问这个地址时就会自动带上cookie，
另外cookie是存储在浏览器本地的

- 这里又说了cookie的同源策略，只有同源才会带上，当然又说了下优化，静态资源可以用子域名，
避免cookie自动发送，减少http消耗

- 又说了下，如果是ajax跨域想带cookie，必须开启withCredentials配置，同时后台也必须开启cors配置

又被问了下前端存储

- sessionstorage，基于tab进程的，tab进程关闭就无效了

- localstorage，最常用的，存储在本地，持久化，但是有最大字节数限制（不同浏览器不一样，可能5m）

- indexdb(sql)，类似于sqllite那种，需要自己封装，创建数据库，写入数据等等，然后会有事务添加回滚，
缺点是某些浏览器，特别是手机浏览器不支持，所以并未应用

又被问了下localstorage的具体细节

- 如果封装一个localstorage，一般会考虑，超过容量后的报错问题，需要try-catch，
关于溢出，不同浏览器可能会有不同处理，譬如写入无效（应用最常见），覆盖等

- 一般封装的库会让API尽量简单，底层细节默认处理，可以给一些回调进行调试错误

- 说了下localstorage可以监听写入事件，这样可以浏览器多个tab间通信

又被问了下http相关

分为三个部分答了下

- 普通的http交互，包括响应码，头部，报文结构

- 跨域场景，譬如跨域cors头部，浏览器预检等

- 缓存场景，etag，cache-control等

然后三个部分都展开讲了下，也别是缓存重点解释了下不同头部

又被问了下web安全

- 提了下sql注入，但没有深入展开

- 介绍了下csrf（跨站身份伪造），应用场景以及防御（referer-但是客户端是不可信的）以及最终方案（token）

- 介绍了下xss（脚本注入），应用场景（输入框，富文本等），浏览器输入URL（一般都有对策），以及防御（不信任输入输出，编码解码）

问了下react

- 说自己由于工作没有接触，业余时间目前正在过vue，不过有计划等vue过完后看react源码

于是掠过了

最后问了一个经典问题：浏览器输入URL到页面加载完成发送了什么

- 思考了下，大概结构是，先说了过主干流程，然后分别展开细节（有些部分不是很详细，但尽量有血有肉，细节都描述）

这个会单独整理成一篇博文，因为内容太多了（最后基本是说到JS引擎解析时就被打断了，boss觉得差不多了，也感觉到了我还有余力）

最后问有什么问题

- 问我最近一年成长的较快，想咨询下根据boss的经历，现阶段有没有什么可以高速成长的建议

回答是：好的平台，好的团队，好的leader（钉钉就挺不错的）

总体来说，整个过程很愉快，boss很彬彬有礼，我也尽量去发挥了（尽量能展开的地方都展开）

整体来说boss应该也挺满意的，我也挺向往的，接下来加油！

## 三面（电话面试-技术面试）

在一个很意外的时间点打电话过来，由于当时环境比较吵就推了一会。过了几个小时候，大概0212，5点30左右打过来。

整体时间：20分钟左右

先问了下：

- 博客是不是自己写的

回答：博客是自己写的，基于jekyll静态模板系统搭建的，所有的内容都是来源于自己平时的技术总结与沉淀。

然后就是直接切入开始问问题了：

- 我现在的团队大概是什么样子的

回答：移动前端团队20人左右，我负责框架开发以及技术支撑，譬如其他人有技术问题都是最终由我出方案或协助解决，
其他人基本都是做项目，包括混合开发项目，微信公众号，钉钉应用等

- 工作怎么样？工作强度，是否辛苦

回答：这公司承接政府项目。我们这边主要做移动APP，总的来说，就工作上强度是一般，所以能够很快的完成任务。
一般我就会利用空闲的时间以及业务时间去学习新技术，沉淀，确保自己不落后。
也会安排业余时间进行学习，确保自己不懒惰写来，不被时代淘汰。

- 谈谈HTTP能否一个链接请求多个资源？

回答：先说了下在现在最常用的http1.1中，请求一个资源就需要开辟一个http请求，如果请求多个资源，就需要多个http请求连接，
而每个http请求的开辟都是很耗时的，因此资源数过多就会卡，所以一般针对这种情况的优化是合并静态资源。
而http2/0的特点就是：多路服用，资源压缩，也就是说一个http连接可以请求若干个资源，当然它还有其它作用，比如压缩资源，可以加快请求速度。

- cookie如何存储敏感信息

回答：（其实第一个回答应该并不是面试官想要的，不过也是一个要点）一般遇到这个需求的话，我会先建议：别再cookie中存储敏感信息，因为太危险了，
然后如果一定要强制存储的话，建议使用RSA等非对称加密技术进行加密

追问：如何阻止别人获取cookie（其实回想下应该是上面提的预设答案吧）

回答：我个人理解应该是阻止别人通过js获取同域名下的cookie，一般这种情况下加上http-only即可，
当然了，如果别人强行hack了浏览器，去获取cookie是没办法的。只能说，客户端并不可信，不要存储重要信息

- 如何让cookie无效

回答：设置cookie的有效期过期即可。cookie是存储在本地的，本质是HTTP请求和后台交互时用的，一般配合后台的session使用，
正常请求都会带上cookie，但是如果设置了它的过期时间为已过期，那么这个cookie就无效了
（另外，过期后是不会自动发送的，而是浏览器如果判断失效后，就会本地删除）

- 如何优化一个h5页面的首屏加载

回答：先说自己由于工作原因，很多优化手段没有付诸于实现，不过自己知道怎么去优化。大致思路是：

首先考虑dns，用dns-prefetch进行局预解析，这样浏览器一有空就会去解析这个dns，接下来的请求就可以减少dns解析的消耗了。
（然后说了下dns解析在移动端比较耗费时间，一般在pc端常用的静态资源拆分多个子域名优化的方案可能在移动端不要使用-这个方案用来解决单个域名的并非请求问题，
而移动端由于域名解析的时间消耗不少，所以一般会将资源合并到单个域名-称之为域名收敛，
当然，一般会配合dns-prefetch使用）

然后就是考虑HTTP请求时的缓存，譬如本地可以用etag，cache-control之类的头部控制缓存
（其实应该详细点展开的，可以谈下HTTP1.0，1.1以及expires，cache-control的区别）

然后就是服务端可以考虑下cdn优化（cdn一般不同地方都会有节点，可以提升访问速度，也可以减少单台的流量压力）

然后就是前端，首先要考虑资源的压缩合并，可以考虑webpack打包，譬如多个js可以分为一个公共的以及一个业务的，css也可以合并。
（这里提了下，css文件数过多可能还会在移动端有丢包问题）

然后说了下css要合理分配，首次在headers中加载的css不要过多，甚至一些重要的可以写入style中
（说了下css并行下载，但会阻塞渲染，所以一般会下载css，构建DOM，然后等css下载完毕后才会构建render树）

然后说了下js的加载，js是会阻塞的，因此不要在headers中加载它
（当然，说了下加上defer和async后可以变为异步）

然后中间穿插了下说首屏加载时，最好只加载一些首屏需要显示的资源，一些无关紧要的资源可以等首屏加载完后处理
（这里忘了提的就是，可以说一些图片什么的可以用懒加载，或者为了体验用骨架屏）

最后，提了下domcontentedload和onload的区别
（domcontentedload是dom构建完毕后，但是图片等资源不一定加载，而onload是所有资源都加载完毕，
所以如有操作，建议放到onload中，
又提了下，避免使用过多的js操作DOM，以免造成过多回流，减慢速度）

忘了提一点，如果是vue，react等spa应用可以考虑ssr服务端渲染，这点对spa很重要

以及服务端后台的gzip压缩（虽然这个一般都是默认开启的）

- 然后问了对node后台了解怎么样

回答：没有时间过，更多是自己学习node时写过一些demo，一般API都是对照文档去看的，没有深入实践
然后就没问了

- 问了下对钉钉的了解

回答：平时可能更多的是技术方面的了解，譬如我们的hybrid框架就是大部分参考钉钉实现的。
对于钉钉的产品理解可能还不够。不过有计划过年这几天去补一下钉钉的产品理解，了解下钉钉的整个历史以及产品功能

- 周末是怎么度过的

回答：一般来说，会用来巩固下自己薄弱的算法，学习下新技术，然后自己会习惯性的总结文章，基本上这样周末时间就能得到尽量充分的利用。
当然，自己还有一个业余爱好：口琴，也会花点时间，核心就是：确保业余不懒惰，不断进步，提升自我。
（忘了提看书之类的，譬如英语书，技术书。。。）

- 问一个算法：一个数组中有两个重复数，如何快速寻找

回答：map法，追问复杂度：O(N)

问了下来杭州有没有问题，有没有女朋友

回答：很向往杭州，目前几年内以事业为主

最后互道了下新年好，结束此次面试

## 四面（电话面试）

很意外的一轮，而且时间比较短（10min左右），总体来说没问什么技术性的问题

而且开头说了下会加我钉钉，发些资料给我的。

- 对小程序是否了解

回答：没有实践过小程序，但是有过一定的了解，然后说了下，它的实现和普通hybrid不一样，而是类似于weex之类的东西

追问：weex那一套和传统的webkit的webview有何不同

回答：我们这边用的都是webkit的webview这一套混合开发，这一套的原理是webview充当浏览器，然后h5嵌套在浏览器端，所以性能较低。
而weex是原生控件，它渲染出来的都是原生view

追问：weex的运行机制大概分析下

回答：首先有一套jscore控制交互，然后前端用js写控件（这里可能是类似于一个固定语法的模板），
然后原生接收到后，进行解析，渲染成原生view（中间的引擎解析可能会比较复杂，譬如和html解析一样，
会包括正则提取，词法分析，构建抽象语法树，代码生成器生成最终view等），
而相比之下webview那一套就是js通过jscore将规则传给原生，原生解析后调用某个原生功能。

面试官：小程序原理这一套要花时间看看，因为目前做的一个平台（大前端）有用到类似于小程序之类的原理

回答：会将这块列入计划的

- 说说自己的职业规划

回答：说了下自己的三年规划，从去年开始，准备3年内专攻技术（前端行业内，尽量做精，做专，做好可以做到topN那种），
所以一般自己都会尽力安排空闲与业余时间来学习技术

- 平时工作辛苦么，加班么

回答：这个公司来说，压力不算很大。但是，自己会尽力利用空余的时间来学习技术，提升自己

- 目前正在学什么

回答：一部分是梳理知识体系，写博客总结。另一部分是看源码，如看vue源码等

- 对哪一个框架比较熟悉

回答：虽然工作上由于某些原因没有实践过，但是目前正在看vue源码（看到了ast，vdom部分左右，之前的一些基本梳理好了），
然后说了下个人规划是vue和react都有列入计划

- 来杭州可以吧？阿里可能会比较辛苦

回答：向往杭州，最近几年已经打算以事业为主的，重要的是能提升个人能力（辛苦倒相对无所谓）

- 问了下多少岁

回答：25

- 有什么问题

问了下进入的话对技术的要求，学习哪方面的

回答：看看小程序原理那块

然后接互道新年好后结束了这次面试

总体来说，这次过后，得把小程序原理这一套列上日程

小程序：

- 核心仍然是js按照特定规则写原生控件语法，然后原生接收到后有一个底层解析引擎解析成原生view

- 实际上，他有可能用的virtual-dom，就跟weex一样，结合vue类似的语法，最终更新到virtual-dom上，然后
vdom上再配合解析成原生view

- 总之，代码上来说，很大一部分借鉴了mvvm的思想

- 而且现在它也推出了部分浏览器中适应的写法

可以看成是一套DSL：Domain Specific Language，做了抽象处理，通过命令/查询式API调用来操作框架。

https://mp.weixin.qq.com/debug/wxadoc/dev/framework/MINA.html

https://zhuanlan.zhihu.com/fedevs

__JavaScriptCore__

JavaScriptCore是一个C++实现的开源项目。使用Apple提供的JavaScriptCore框架，
你可以在Objective-C或者基于C的程序中执行Javascript代码，也可以向JavaScript环境中插入一些自定义的对象。
JavaScriptCore从iOS 7.0之后可以直接使用。

Android中使用JS Engine（V8）进行双向通信（小程序中则有可能利用x5内核），运行在JSBridge线程中。

## 五面（电话面试-业务【开放平台】）

确实很意外这一天又收到了一个电话面试，这次是偏业务性质，以及聊了下钉钉那边的工作情况（30min左右）。

这次有不少内容直接就没记住。。。

- 为何选择钉钉

回答：是在segmentfault上收到内推信，然后我对阿里挺向往的，以及恰好由于工作原因有接触过钉钉，
譬如这边做了一个hybrid框架，也是大部分参考的钉钉实现的，所以还是对钉钉蛮有好感的，就想试一试。

- 有没有职业规划

回答：从去年开始，3年内以技术深度为主（目前是领域专家），然后会逐渐拓宽自己的广度，往架构上靠。

追问：对架构方面的了解

回答：目前可能没有专门去了解，更多的是平时的涉猎，不过准备当技术答到一定层次后，梳理知识骨架，然后填充内容，这样更容易一些

- 问了下目前的技术情况，是一毕业就做前端的么？

回答：不是，我在大学时还做过unity游戏开发，后来毕业时是做Android（学了半年左右，现在可能忘了不少，但是仍然能看懂代码，
这点对我帮助很大，譬如做hybrid框架时就很有优势），
然后工作1，2个月后就前端，目前主要专精方向是前端
（强调了下是自学，没有培训，还有学过不少东西）

- 自己公司的情况（业务）

回答：这个公司是承接政府项目，我们这边是做移动前端开发，整个前端团队大概20人左右，我个人的做框架开发以及技术支撑，
其它人更多的是做项目，然后有不会的问题或者新技术都有我这边处理或者出方案（譬如跨域）

又回答了下：在公司大概是第一年从项目中成长，然后到第二年开始成熟后逐渐做框架开发和技术支撑

- 有没有带团队

回答：主要的工作仍然是技术相关，所以并没有参与管理，譬如团队20人左右，是分为不同的小组管理，
我则是提供统一的框架支撑和技术支撑（说了下认为目前的核心竞争力还是技术）

- 对钉钉的了解

回答：更多的是技术方面，譬如我们这边的hybrid框架就是参考钉钉的，很多的API设计，文档编写。
对于产品方面，最近又开始尝试使用一些钉钉的功能

- 平时怎么学习的

回答：工作之余，会安排时间学习新技术，譬如会定期专攻某个知识点，总结成博客，然后会看下源码，譬如最近有看vue源码，
然后会看下技术书籍，当然自己英语比较薄弱，也有开始培养自己看英语书的习惯，
当然自己还有一门业余爱好，口琴，也会花一点时间

追问：锻炼怎么样。。。

回答：可能就是做50个仰卧起坐和俯卧撑，其它的锻炼可能暂时没有（因为时间已经挺满的了，后续可以考虑重新规划）

- 然后面试官说了下钉钉的一些情况：

工作比较辛苦（长期10小时以上，要有心理准备）

飞速发展，迭代很快，譬如每4周就要出新版本迭代（就跟打仗一样，比较累）

发展很快速，成长空间很大，但是可能很多都是新踩坑的，以前经验不一定派的上用处，需要学习主动性，要不然容易掉队

聪明的人很多，有淘汰机制，如果跟不上就容易淘汰，当然，如果能力出色，也容易脱颖而出

整体来说，需要对业务有深入了解，否则可能最事情比较局限，而且更新很快速（业务了解深，才能确保）

比较累，进来时需要先做好心理准备

而且由于挑战比较大，所以前面也为什么问了平时的学习，因为平时要主动学习各种新知识，这样才能确保不掉队

举了个例子，譬如接到一个VPN需求，这时就算你平时不是做这个的，也得给客户出一个解决方案

而且平时也不会要求说做什么做什么，但是总体按业务来看，做的不好就容易掉队

有强调了下：成长空间很大，会接触很多的领域新知识

回答：已经做好了心理预期，未来这几年以事业为主，只要个人发展空间足，已经做了心理准备，也想挑战下自己的潜力

- 工作地点，基本情况

回答：工作苏州附近，老家外省（湖南），93年11月

然后问了下面试官问题：对加入钉钉之前的技术储备，有没有什么建议，可以提前准备

面试官：建议将整个钉钉产品熟悉，特别是开放平台这一块可以熟悉下，文档看一看，直到有什么业务与功能，
然后就是开放平台的企业组织这一块了解一下（譬如这个公司承接的是政府项目，其实政府也可以算是某一类组织）。
说了下，如果hr发了offer，可以去先了解下业务

最后互道新年好后结束了此次面试

为什么有4-5面，总体有两种可能：

1. 前面几次都是技术筛选，合格后才到第5面（对应业务线的直属leader），然后了解情况

2. 4-5面时可能由不同业务条线的人来面，以决定最终加入哪一个（因为感觉4是偏技术，5偏业务）

技术与业务：

- 技术服务于业务，最终的技术努力一定要在业务上对用户产生价值

- 需求是永远都做不完的，不可能所有需求都做，也不是所有的需求都一定要做

- 工程师不是完成业务的“资源”，我们的责任是将如何解决单一问题，变成系统化解决一类问题

所以最重要的是解决问题的能力，技术的本质也是方便去解决问题