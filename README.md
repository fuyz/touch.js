# touch.js
Touch
在开发移动端的应用中会使用到很多的手势操作，例如一指拖动、两指旋转等等，为了方便开放者快速集成这些手势，在Clouda中内置了事件和手势库Library.touch，下面将详细的介绍如何使用Library.touch。

手势事件处理类API目前支持以下功能：

    事件配置
    事件代理
    事件绑定
    解除事件代理
    解除事件绑定
    触发事件
    事件配置

touch.config(config)

功能描述：

对手势事件库进行全局配置。

参数描述：

    config为一个对象

    {
        tap: true,                  //tap类事件开关, 默认为true
        doubleTap: true,            //doubleTap事件开关， 默认为true
        hold: true,                 //hold事件开关, 默认为true
        holdTime: 650,              //hold时间长度
        swipe: true,                //swipe事件开关
        swipeTime: 300,             //触发swipe事件的最大时长
        swipeMinDistance: 18,       //swipe移动最小距离
        swipeFactor: 5,             //加速因子, 值越大变化速率越快
        drag: true,                 //drag事件开关
        pinch: true,                //pinch类事件开关
    }
    
事件代理

    touch.on( delegateElement, types, selector, callback );

功能描述：

事件代理方法。

参数描述：

    参数	类型	描述
    delegateElement	element或string	事件代理元素或选择器
    types	string	手势事件的类型, 可接受多个事件以空格分开；支持原生事件的透传。目前支持的具体事件类型，详见《手势事件类型》。
    selector	string	代理子元素选择器,
    callback	function	事件处理函数，如需了解手势库支持的新属性，详见《事件对象》
    **

手势事件类型

**

支持的手势事件类型：

        分类	参数	描述
    缩放	
        pinchstart	缩放手势起点
        pinchend	缩放手势终点
        pinch	    缩放手势
        pinchin 	收缩
        pinchout	放大
    旋转	
        rotateleft	向左旋转
        rotateright	向右旋转
        rotate	    旋转
    滑动	
        swipestart	滑动手势起点
        swiping	    滑动中
        swipeend	滑动手势终点
        swipeleft	向左滑动
        swiperight	向右滑动
        swipeup	    向上滑动
        swipedown	向下滑动
        swipe	滑动
    拖动
        拖动开始   dragstart	拖动屏幕
        拖动	    drag	拖动手势
        拖动结束   dragend	拖动屏幕
        拖动	    drag	拖动手势
        长按	    hold	长按屏幕
        敲击	    tap	    单击屏幕
        doubletap	双击屏幕
        
更多使用实例请参考http://code.baidu.com

**事件对象**

事件处理函数的第一个参数为事件对象，除了原生属性之外，百度手势库还提供了部分新属性。

以下为手势新增的属性：

        属性	描述
        originEvent	触发某事件的原生对象
        type	事件的名称
        rotation	旋转角度
        scale	缩放比例
        direction	操作的方向属性
        fingersCount	操作的手势数量
        position	相关位置信息, 不同的操作产生不同的位置信息
        distance	swipe类两点之间的位移
        distanceX, x	手势事件x方向的位移值, 向左移动时为负数
        distanceY, y	手势事件y方向的位移值, 向上移动时为负数
        angle	rotate事件触发时旋转的角度
        duration	touchstart 与 touchend之间的时间戳
        factor	swipe事件加速度因子
        startRotate	启动单指旋转方法，在某个元素的touchstart触发时调用
        
事件绑定

    touch.on( element, types, callback );

功能描述：

事件绑定方法，根据参数区分事件绑定和事件代理。

参数描述：

    参数	类型	描述
    element	element或string	事件绑定元素或选择器
    types	string	事件的类型, 可接受多个事件以空格分开，支持原生事件的透传。具体参数说明，同“事件代理”方法中的“types”参数说明。
    callback	function	事件处理函数，具体参数说明，同“事件代理”方法中的“callback”参数说明。
    
解除事件代理

    touch.off( delegateElement, types, selector, callback )
    
功能描述：

解除某元素上的事件代理。

参数描述：

    参数	类型	描述
    delegateElement	element或string	元素对象或选择器
    types	string	事件的类型，具体参数说明，同“事件代理”方法中的“types”参数说明。
    selector	string	代理子元素选择器
    callback	function	事件处理函数, 移除函数与绑定函数必须为同一引用。具体参数说明，同“事件代理”方法中的“callback”参数说明。
解除事件绑定

    touch.off( element, types, callback )
    
功能描述：

解除某元素上的事件绑定，根据参数区分事件绑定和事件代理。

参数描述：

    参数	类型	描述
    element	element或string	元素对象、选择器
    types	string	事件的类型，具体参数说明，同“事件代理”方法中的“types”参数说明。
    callback	function	事件处理函数, 移除函数与绑定函数必须为同一引用;具体参数说明，同“事件代理”方法中的“callback”参数说明。
    
触发事件

    touch.trigger(element, type);
    
功能描述：

触发某个元素上的某事件。

参数描述：

    参数	类型	描述
    element	element或string	元素对象或选择器
    type	string	事件的类型，具体参数说明，同“事件代理”方法中的“types”参数说明。
