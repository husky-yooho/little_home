Java基础

Java四种引用类型
ReferenceQueue的作用
类的继承关系，域的覆盖，static，private
抽象类和接口的区别
反射(不调用构造创建实例)，注解的使用(注解处理器)
Android中hide方法的调用
final修饰的变量可以被反射么？
泛型
HashMap 实现原理
equals 与 hashcode 关系
并发，volatile 关键字作用
synchronized关键字用于static方法和成员方法的区别
生产者，消费者
网络tcp, udp
序列化和反序列化
四种访问权限的区别

Android基础
layout_gravity和gravity的区别
动画，属性动画原理
touch事件分发
view绘制流程
activity生命周期
fragment生命周期
有几种launchMode，区别是什么
Handler机制,HandlerThread
targetSdkVersion的作用
广播类型
启动service方式
service运行在哪个线程
IntentService作用, 运行在非UI线程
LocalBroadcastManager发送的广播和Context发送的广播有什么区别？
AsyncTask
Dialog是否可以使用非Activity的Context  Application context不可以，为什么不可以？Dialog必须依赖一个token

Looper#loop() 后是否可以写代码

mHandler.post(new Runnable() {
    public void run() {
        Log.d("TAG", "A");
    }
});
Log.d("TAG", "B");

高工
ListView的优化
启动速度优化
自定义View常见覆盖的方法：onDraw, onLayout, onMeasure, onFinishInflate, onSizeChanged
touch事件分发的过程：onInterceptTouchEvent，dispatchTouchEvent，onTouchEvent
动画的执行过程
ActivityContext、ApplicationContext、ViewContext和BaseContext的区别
View绘制流程，一定不能在非UI线程更新UI吗？
View添加到Window的时机
Handler机制
广播类型：普通广播，有序广播，粘性广播，区别
加载大图如何避免OOM
常见避免OOM的方式
bitmap内存计算
圆角图片实现 
图片加载库设计，内存泄露工具，性能优化工具
常用网络库强引用
2. 弱引用
3. 弱引用
4. 虚引用
Android JsBridge实现原理（Webview jsbridge的漏洞）
Android中IPC机制：Binder机制，匿名共享内存，默认16个线程
multidex，65535
push设计：http://blog.csdn.net/a345017062/article/details/8648205，心跳包，长连接
多线程断点续传的实现：http://my.oschina.net/u/141149/blog/55337
设计打点统计时长的库

网络
tcp和udp的区别，tcp三次握手和四次挥手
get和post请求的区别
https通信过程
常用的http错误码

其他
设计模式和Android中的使用场景
sqlite 数据库优化，索引是什么，db中左外连接和右外连接的区别


没准备：
TextView实现原理：BoringLayout用于单行不可变文本，DynamicLayout用于可变化的文本，但是布局效率更低，StaticLayout用于不变的文本，布局效率高




#### java基础

1. Java四种引用类型
	1. 强引用。	OOM都不回清掉。就是平时用的 A a = new A();
	2. 软引用。	当内存不足时，回来清理这部分。非常适合做缓存功能
	3. 弱引用。	JVM的GC定时回收的部分
	4. 虚引用。	使用时候会绑定一个队列，观察队列，可以知道GC什么时候开始执行了

2. ReferenceQueue的作用
	1. 将要被回收的

3. 类的继承关系，域的覆盖，static，private
	1. public、protect、default、private

4. 抽象类和接口的区别
	1. 包含的方法。	可以有实现
	2. 访问修饰符。	接口必须全部是public
	3. 成员变量。		接口只能是，public static final的
	4. 继承和实现		抽象类可以继承一个类和实现多个接口。	接口只能继承一个或多个接口

5. 反射(不调用构造创建实例)
	1. 通过包名获得到对应的类，调用对应的方法可以获得对应的成员变量，方法函数，构造函数
	2. 可以调用构造函数（newInstance），调用普通函数（invoke（对象，值）），改变成员变量的值

6. 注解的使用(注解处理器)
	1. 元注解
		1. @Target：		指定了注解可以给哪些对象用
		2. @Retention	指定了注解的生效时间周期（source、class、runtime）
		3. @Documented	此注解将被javac工具提取生成文档
		4. @Inherited	允许子类继承父类中的注解

7. Android中hide方法的调用
	1. 反射

8. final修饰的变量可以被反射么？
	0. 可以，但是是否可以获得到，要看情况（是否被自动优化）
	1. final在方法需要返回时，会执行自动优化，return this.name，直接将final的值返回
	2. 如何避免：return null != null ? "ddd": this.name

9. 泛型
	1. <T> 可以用在类上，方法返回值，入参，成员变量上

10. HashMap 实现原理
	0. 先计算hash值，然后是map机制
	1. hashmap，是线程不安全的（没同步）
	2. hashmap的key和value可以是空
	3. hashmap重新计算hash值
	4. 替换备选sparseArray，ArrayMap（key强制为int类型，二分法，数据千级以内）

11. equals 与 hashcode 关系
	1. equals相同则hashcode一定一致，hashcode一致equals不一定一致

12. 并发，volatile 关键字作用
	1. synchronized同步锁，在方法名上加；加同步锁传入一个对象
	2. 原子性，可见性，有序性（解决了后两者）。强制线程引用重新到内存里重新取值

13. synchronized关键字用于static方法和成员方法的区别
	1. 对于静态方法，持有的是类对象，对于非静态持有的是对象实例
	2. 影响的同步域不一样。

14. 生产者，消费者
	1. 解决同步的问题，线程等待与阻塞

15. 网络tcp, udp
	1. tcp：传输控制协议，面向连接
	2. udp：用户数据包协议，无连接协议

16. 序列化和反序列化
	1. 实现serializable：		serializableId
	2. 实现externalizable：		重写writeexternalizable，readExternalizable（对象不然会被初始化）


#### 安卓基础
1. gravity，layout_gravity：区别
	1. gravity： 		是viewgroupo决定子控件布局的
	2. layout_gravity：	是决定自己在父控件的布局

2. 动画，属性动画原理
	1. view动画：	补间动画translate、scale、rotate、alpha、set
		1. 在anim -- xml文件里写文件。
		2. AnimationUtils.loadAnimation(context, R.anim.xxx)
			view.startAnimation(animation)
	2. 帧动画：		在anim -- xml文件里写，animation-list
	3. 属性动画:		可以写在anim -- xml文件里，animator，然后在代码里调用
		```
		anim = ObjectAnimation.ofint(view, "name", startVal, endVal)
		anim.setDuration(int)
		anim.setRepeatMode(..)
		anim.star();
		配合onDraw() 实现动画
		// 启动动画
		```
3. touch事件分发
	1. dispatchTouchEvent:	派遣事件？true表示消费掉，false表示不处理丢回去，super表示继续下传
	2. onInterceptTouchEvent：拦截事件？true，表示自己处理，false表示不处理下传
	3. onTouchEvent：执行如何处理，返回true，表示不通知父处理

4. view绘制流程
	1. measure过程：onMeasure在measure过程中被调用
		1. 根据规则测量child元素，getChildMeasureSpec方法得到measureSpec
		2. 调用child的measure方法
		3. setMeasureDimension确定最终大小
	2. layout过程：当viewGroup的位置被确定后，遍历子元素，并调用其layout方法
		1. layout确定自身位置，onLayout确定子元素位置
		2. 获取父padding边界的值，子view的布局参数
		3. 调用child.layout方法，对子ciew进行布局

5. activity生命周期
	1. onCreate，onStart，onResume；创建、可见、获得焦点
	2. onDestory，onStop，onPause
	3. onSaveInstanceState，3之后再onPause方法中调用
	4. onRestoreInstanceState，在onStart和onResume之间

6. fragment生命周期
	1. onAttach, onCreate, onCreateView, onActivityCreate
	2. onStart, onResume, 
	3. onPause, onStop
	4. onDestoryView, onDestory, onDetach

	5. fragment的使用：（pageView）
		1. 通过 fragmentManager 管理，通过commit生效
			1. add
			2. hide，show
			3. remove		：删除，并销毁fragment
			4. replace		：remove + add
			5. detach、attach

7. 有几种launchMode，区别是什么
	1. standard：	标准模式
	2. singleTop：	只有act是栈顶，才不创建新的
	3. singleTask：	
		1. 没有创建新的任务栈，taskID一致
		2. 如果已经在栈中，会调用该Act的onNewIntent方法
		3. 清除该act之上的说有其他act
	4. singleInstance：
		1. 新的任务栈，单独个一个实例
		2. 其他的act不能进这个栈

8. Handler机制,HandlerThread
	1. Looper，handler， messageQueue
	2. 建立个子线程，用子线程里的looper来分担主线程的任务
	3. 子线程的任务队列，线性排队

9. targetSdkVersion的作用
	1. targetSdkVersion:指定程序运行时，是按照那个版本的情况去执行的
	2. target：project.propertise文件中的，用于决定用哪个版本去编译

10. 广播类型
	1. 普通广播
		1. 在AMS中注册：静态注册，动态注册
			1. 静态注册：设置enable，exported，procee，intent-filter
			2. BrocastReceiver, IntentFilter
			3. 何时注销：onResume, onPause。有可能onPause后act就被销毁
		2. onReceive方法：运行在主线程，不能做耗时操作
		3. 发送广播：intent，sendBrocast
		```
		Intent intent = new Intent();
		//对应BroadcastReceiver中intentFilter的action
		intent.setAction(BROADCAST_ACTION);
		//发送广播
		sendBroadcast(intent);
		```
	2. 系统广播
	3. 有序广播：接收者是按先后顺序接受的，可以拦截、可以修改
	4. 应用内广播：exported = false

11. 启动service方式
	1. startSertvice -- stopService & stopSelf
		1. onCreate: 		只有service没创建时候才会调用，不会一致被调用
		2. onStartCommand：	每次都会被调用(return )
			1. start_not_sticky			：被回收后不被重建
			2. start_sticky 			：被回收后重建
			3. start_redeliver_intent	：重建后得到intent
		3. onBind:			抽象方法需要重写（start方式并用不到）
		4. onDestory：		销毁时执行
	2. bindService：	使用的C/S模式。client是activity，多个C绑定到一个S上
		1. 当C销毁时，自动与S解绑，也可以unbindService解绑
		2. 当没有任何C与S绑定时，S自行销毁
	3. service如何不被杀死：
		1. onStartCommand的返回值
		2. 提升service优先级
		3. 提升service进程的优先级
			1. 前台进程
			2. 可视化进程
			3. 次要服务进程
			4. 后台进程
			5. 内容提供者
			6. 空进程
	4. IntentService作用, 运行在非UI线程
		1. 不需要自己去创建thread
		2. 不需要高绿什么时候该关闭service

12. AsyncTask
	1. 封装了两个线程池（serialExecutor，Thread_poll_excutor），一个handler
	2. 过程方法
		1. onPreExecute：	主线程执行，任务开始前执行
		2. doInBackground：	子线程执行，做耗时操作
		3. publishProgress：	在子线程调用，会马上执行onProgressUpdate
		4. onProgressUpdate：主线程执行
		5. onPostExecute：	主线程执行，将doInbackground的返回值传入，更新主线程的结果

13. 线程池
	1. 好处：降低资源的消耗，最大限度服用，提升响应速度
	2. new ThreadPollExecutor（）
		1. coreRoolSize：	核心线程数量，闲置也不销毁，与keepAliveTime关联
		2. maximumPoolSize：	最大线程数量，任务超过max后新任务被阻塞。
		3. keepAliveTime：	影响非核心线程闲置销毁时间，当allowCoreThreadTimeOut为true时，这个超时设置会对核心线程产生效果。
		4. unit：	对keepAliveTime设置单位，是枚举类型，天、分钟...
		5. workQueue：	被阻塞的任务队列
		6. threadFactory：	线程工厂，接口类型，需实现newThread方法
		7. handler：		当任务满了的时候，会去执行对应的处理操作
	3. 四种线程池类
		1. FixedThreadPool		：设置最大线程数就是核心线程数，线程都不会被回收，能够快速响应外界请求
		2. CachedThreadPool		：没有核心线程数，用响应速度来换取了内存性能
		3. ScheduleThreadPool	：核心线程数固定，对非核心线程没有限制，且当非核心线程处于限制状态的时候就会被立即回收，适用于定时任务
		4. SingleThreadPool		：一个时间只会有一个任务在执行k

14. Dialog是否可以使用非Activity的Context  Application 
	1. window的type类型：
		1. 应用窗口：
			activity
		2. 子窗口：
			1. popupWindow
			2. contextMenu
			3. optionMenu
		3. 系统窗口
			1. toast
	2. setContentView本质是把DecorView作为子view添加到PhoneWindow的DecorView中
	3. dialog的show是需要一个token的，为了安全起见



#### 安卓高工
1. listview优化
	1. convertView
	2. viewHolder
	3. 监听listView滑动状态，滑动时不加载图片
	4. onCLickListener处理，在viewHolder上设置监听，不要每次getView设置
	5. 减少item view布局层级。布局深会在绘制时浪费大量资源
	6. getView方法中尽量减少使用逻辑、减少耗时操作，减少大对象
	7. 将listView的scrollingCache，animateCache设置为false

2. 启动速度优化
	1. 代码优化：			application的onCreate方法里不要做很复杂的事情
	2. traceView工具：	在oncreate中加Debug.startMethodTracing（“sss”），分析“sss.trace文件”
	3. DDMS分析trace文件
	4. application的onCreate中耗时操作放在serviceIntent里面
	5. 使用splashActivity：什么都不渲染，给一个背景

3. 动画，属性动画原理
	1. 好处
		1. 打破只能更改view的局限
		2. 真正的改变了对象的属性
		3. 让动画效果更丰富
	2. 原理：
		1. 不断的控制值的变化，在不断的手动赋给对象的属性

4. 自定义View常见覆盖的方法：onDraw, , 
	1. onMeasure,
	2. onLayout
	3. onDraw
	4. onFinishInflate：	当xml文件填充完会执行回调，如果是new出来的则不调用
	5. onSizeChanged

5. touch事件分发的过程：
	1. onInterceptTouchEvent： 	是否拦截
	2. dispatchTouchEvent：		是否分发
	3. onTouchEvent

5. ActivityContext、ApplicationContext、ViewContext和BaseContext的区别
	1. application只会有一个
	2. act、service的baseContext都会是新的
	3. viewContext一般都是activity.this

6. View绘制流程，一定不能在非UI线程更新UI吗？
	1. 不是。
	2. 当Activity对象被创建完毕后，会创建ViewRootImpl对象,mThread 是在ViewRootImpl 的构造方法里这样初始化的。mThread为主线程
	3. 在onResume之前，没有ViewRootImpl，所以检查不了线程问题
	4. 使用一个新的viewRootImpl去增加视图

7. 粘性广播：
	1. manifest声明时字段不一致
	2. 粘性广播可以发送广播先发出去，只要不被消费就会存在系统里，后去注册，也可以接收到广播

8. 加载大图如何避免OOM
	1. 使用BitmapFactory.decodeResource(getResource(), R.id.image, BitmapFactory.Options)
	2. Options:
		1. inJustDecodeBounds = true
		2. inSampleSize = 0.2
	3. LRUCache缓存机制，将移除屏幕的图片进行回收

常见避免OOM的方式
bitmap内存计算
圆角图片实现 
图片加载库设计，内存泄露工具，性能优化工具
常用网络库强引用
2. 弱引用
3. 弱引用
4. 虚引用
Android JsBridge实现原理（Webview jsbridge的漏洞）
Android中IPC机制：Binder机制，匿名共享内存，默认16个线程



1. 内存泄漏
	1. leakCanary：
	2. 原因：
		1. 单例模型持有activity：	
			1. 单例的静态实例特性，如果持有context就会无法释放
			2. 持有application的context
			2. 弱引用
		2. 非静态内部类持有外部类引用：
			1. activity的handler持有acitiy
				1. 在acitivity销毁时，
				2. 清除掉所有的callback和message
			2. 线程泄漏
				1. 异步、子线程持有act的context
				2. 在activity销毁时，执行asyncTask.cancel（）
			4. 内部类+内部类的静态实例
				1. 内部类持有外部类act，导致不能被释放
				2. 将内部类改成静态内部类
			5. Timer，Timertask
			6. 集合中的对象，及时remove掉
			7. 
		3. webview加载资源
			1. 为了加载速度快，webview会持有很多个页面，无法销毁掉，用了application的context
			2. 将webview单独放在一个进程，检测掉内存大时，直接kill进程
		4. 资源未关闭
			1. braodcastReceiver
			2. contentObserver
			3. Timer，TimerTask
			4. 集合中持有对象，没有及时remove掉
			3. File
			4. 属性动画，mAnimation.cancel()，不然会一直播下去
			4. Cursor
			5. Stream
			6. Bitmap。调用recycle（）
		5. webview的优化：
			0. mWebViewContainer.removeView(mWebView)
			1. mWebView.stopLoading
			2. mWebView.getSettings().setJavaScriptEnable(false)
			3. mWebView.clearHistory
			4. mWebView.removeAllViews()
			5. mWebView.destory()
2. SurfaceView
	1. 独立的绘制表面，不与主窗口共用一个绘图表面，可以单独在一个线程绘制
	2. 和view的区别
		1. surfaceView更适用于被动的频繁的刷新动作，viwe适用于主动的
		2. surface适用于子线程对页面进行刷新
		3. surface实现了双缓冲机制
	3. 使用：
		1. 继承surfaceView
		2. 实现surfaceHolder.callback的三个方法：
			1. surfaceCreated		：开一个子线程绘图，while循环调draw（）
			2. surfaceChanged
			3. surfaceDestoryed		：将wihle断开

3. window，activity，view
	1. activity：控制模型，控制window
	   window：承载模型，负责承载视图
	   view：显示模型，用于显示
   	2. activity与window：
   		1. 在acrtivity实例后，调用attach方法，并执行到回调
   		2. window与view：
   			1. viewRoot：是viewtree的管理则
   			2. DecorView是viewTree的根节点
   			3. Decorview添加入window中
		3. 设置全屏，需要操作windowsManager，对其设置falg

4. MVVM，V + M + VM，DataBinding
	1. V：只做UI相关的内容，不处理任何业务逻辑，只做UI自己的逻辑
	2. VM：只做逻辑，不做任何UI相关的事情
		1. Context
		2. Model
		3. DataField
		4. Command
		5. Child ViewModel
	3. M

leakCanary是Square开源框架，是一个Android和Java的内存泄露检测库，如果检测到某个 activity 有内存泄露，LeakCanary 就是自动地显示一个通知，所以可以把它理解为傻瓜式的内存泄露检测工具。通过它可以大幅度减少开发中遇到的oom问题，大大提高APP的质量。






#### 自定义关心内容
1. 堆和栈
	1. 栈内存：存放局部变量
	2. 堆内存：是存放数组，对象

2. Dalvik和标准JVM的差别
	1. Dalvik：+JIT（2.2）
		1. 基于65536个寄存器，减少编译的时间
		2. 生成的.dex文件（基本元素：常量池，类定义，数据段，实例变量）
			1. 减少文件尺寸
			2. 提高IO操作速度，编译速度
		3. dalvik会有一个单独的linux进程执行
		4. 

	2. JVM
		1. 基于栈，变量放置在局部变量表中，被压入堆栈中共操作码运行
		2. 生成class文件

	3. ART（4.4之后引入，5.0成为正式VM）
		1. 引入AOT（ahead-of-time）预编译技术：dex2aot，把字节码编译成机器码
		2. GC效率的优化，将两次GC变为一次，提升GC工程学，减少后台内存和内存碎片
		3. ART需要在应用安装时，把程序代码转换成机器语言，所以会消耗掉更多的存储空间，20%以内
		4. 有转码过程，所以安装时间会更长

3. application启动过程
	1. bootloader启动内核，init进程，init分裂出来守护进程，提供底层服务
	2. init启动Zygote进程，其初始化第一个VM，并预加载framework和APP需要的通用资源，开启socket监听请求，VM来管理新的APP继承
	3. Zygote启动之后，init继承会启动runtime进程，孵化出一个超级进程--System Service，启动所有核心服务各种manager、硬件service，并启动第一个APP进程HOME

	4. 在HOME上点击一个activty图标
		1. startActivity，通过Binder IPC调用到ActivityManagerServervice
		2. packageManager手机intent的指向信息
		3. 判断权限是否足够去访问指向的activity
		4. 权限足够的话，activityManager会启动新的task启动目标activity
		5. 检查processRecord是否存在，不存在的话就新建进程

	5. 创建进程
		1. activityManagerService调用startProcessLocked（），通过socket传递参数给Zygote，Zygote孵化自身，调用ZygoteInit.main()，返回进程pid
		2. ActivityThread调用Looper.prepareLoop，和Looper.loor（）循环消息
		3. application和进程绑定
		4. 进程内启动activity，调用realStartActivity，sheduleLaunchActivity（）发送一个LAUNCH_ACTIVITY


4. 内存泄漏



5. 所有到的技术：
	1.  google提供的新的dataBinding技术
	2.  xml. activity, viewModel, model, handler, event
	3.  数据向UI：notifyPropertyChanged(BR.firstName)
	4.  UI向数据：可以在xml中增加监听



5. recycleView
	1. 背景
		1. 在support-v7中出现
		2. 封装了ViewHolder，Adapter面向ViewHolder而不再是view，复用逻辑被封装起来了
		3. 提供了一种插拔式体验，高度解耦，异常灵活
		4. 可控制Item增删的动画，ItemAnimation这个类进行控制
	2. 主要封装类
		1. 控制其显示方式，通过LayoutManager
		2. 控制Item间隔，通过ItemDecoration
		3. 控制Item增删动画，通过ItemAnimator
		4. 各种点击事件，只能自己回调
		5. 控制Item增删，只能自己Mark
	
6. drawable
	1. bitmap
	2. shape
		1. android:shape = rectangle, oval, line, ring
		2. corners(圆角)
		3. solid(填充色)
		4. gradient(梯度，渐变色)
			1. angle：渐变的角度
			2. startColort、centerColor、endColor
			3. type：渐变类型（liner/radial/sweep）
			4. gradientRadius，渐变半径
			5. centerX/centerY，渐变中心点
		5. stroke（描边）
			1. width，描边宽度
			2. color，描边颜色
			3. dashWidth，虚实线，实线的长度
			4. dashGap，间隔宽度
		6. size
	3. layer-list
		```
		<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    		<item>
        		<shape android:shape="rectangle">
            		<solid android:color="#0ac39e" />
        		</shape>
    		</item>
    		<item android:bottom="7dp">
        		<shape android:shape="rectangle">
            		<solid android:color="@android:color/white" />
        		</shape>
    		</item>
    		<item
        		android:bottom="2dp"
        		android:left="2dp"
        		android:right="2dp">
       			<shape android:shape="rectangle">
           			<solid android:color="@android:color/white"/>
       			</shape>
   			</item>
		</layer-list>

		```
	4. StateListDrawable
		1. android:state_pressed
		2. focused
		3. checked
		4. enable
	5. transitionDrawable
		1. transition标签













