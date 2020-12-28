# Interview

1.如果一个第三方SDK 产生空指针问题而崩溃，如何解决？

    解压缩jar，修改报错类文件,重打包jar文件

2.让你设计一套架构

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
    
    
