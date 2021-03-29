# Interview

1.如果一个第三方SDK 产生空指针问题而崩溃，如何解决？

    1.字节码插桩技术实现
    2.解压缩jar，修改报错类文件,重打包jar文件；
    
1.Java使用同步的方式？

    synchronized Lock LockSupport Cas ThreadLocal 
    
2.Android 如何处理兼容性API接口调用？

    1.比如某机型接口参数不同
    try{
        标准调用();
    }catch(Exception e){
        异常精准调用();
        异常模糊调用();
        一般模糊调用();
    }
    
    2.标准接口使用SDK_INT > x 判断
    
    3.反射调用某方法是否存在

3.让你设计一套架构

    标准化/模板化,策略化,配置化，动态化
    
    标准化/模板化：每个AppBusModule都规定如何实现
    
    策略化：每种SDK可以添加1中或者多种策略（比如支付SDK，可以同时集成一种或者集中，并且只要一个配置即可）
    
    配置化:App壳可以动态配置不同的AppBusModule，取决与具体的业务，做到动态配置打包
    
    动态化:做到后台可控制，哪些App业务模块可进行展示
    
    AppBaseModule:
            Base_Core_Util
            Base_Core_UI
            Base_Core_Widget
            
    AppSDKModule:      
            App_SDK_Video
                App_SDK_FFMpeg
                App_SDK_OpenCV
                
            App_SDK_NET
                App_SDK_NET_OKHTTP
                App_SDK_NET_Volley
                App_SDK_NET_Retrofit
                
            App_SDK_Pay
                App_SDK_Pay_GOOGLE
                App_SDK_Pay_Huawei
                App_SDK_Pay_ZFB
                App_SDK_Pay_TX
               
            App_SDK_AD
                App_SDK_AD_GOOGLE
                App_SDK_AD_FACEBOOK
                App_SDK_AD_Twitter
                App_SDK_AD_MI

    AppBusModule:
            App_News --> AppSDKModule(每种SDK1+)   + AppBaseModule
            App_IM   --> AppSDKModule(每种SDK1+)   + AppBaseModule
            APP_Game --> AppSDKModule(每种SDK1+)   + AppBaseModule
            
    App壳：AppBusModule + AppBusModule + AppBusModule，也即AppBusModule集合
    
    
