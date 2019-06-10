# iPad Pro (11-inch)  iPad Pro (12.0-in) (3rd generation) 启动图适配

## 背景

启动图的适配是一个头疼的问题，尤其是对于同时适用iPhone,iPad的APP来说。苹果发布了iPad Pro (11-inch)，iPad Pro(12.0-inch) 之后，我发现我的app出现了**上下黑边**，遇到这个问题，我第一反应想到的就是在**Asset catalog**中的LaunchImage里面设置，但是我发现**Asset catalog**里面的**launchImage** 里面根本就没有针对`iPad Pro (11-inch)  iPad Pro (12.0-in) (3rd generation)` 启动图的设置，针对iPad的启动图的设置只有一个

## 解决方案

有2种方法可以尝试，本文推荐第二种，图片不会拉升，你也可以尝试第一种
1. 使用LanchScreen.storyBoard来设置
2. 使用xcode的plist文件来设置
   
### 使用**LanchScreen.storyBoard**来设置

使用这个方式设置的缺点就是可能图片有拉升，在LaunchScreen.storyBoard中放一个ImageView充满整个页面，然后设置图片，这个方法的缺点是图片可能会**拉升**，但是好处是，将来**无论出现什么分辨率**的设备，都能适配，这个方法不会拉升图片

    Xcode->Targets->General->App Icons and Launch Images->Don’t use asset catalogs
        Xcode->Targets->General->App Icons and Launch Images->Launch Screen File->LaunchScreen.storyBoard

### 使用xcode的**plist**文件来设置

xcode的plist文件有很多配置项，也可以配置启动图，这个方法不会拉升图片，以下是配置步骤

1. 设置xcode启动图
2. 设置plist文件
3. 准备启动图
4. 检查启动图对应尺寸

#### 设置xcode启动图

该选项表示不适用xcode的asset catalogs，这样设置之后可以删除Asset catalog里面的Launch Image了

    Xcode->Targets->General->App Icons and Launch Images->Don’t use asset catalogs

#### 设置plist文件

找到plist文件，右键选择View as sourceCode,在文件中插入以下内容

    <key>UILaunchImages</key>
        <array>
            <dict>
                <key>UILaunchImageMinimumOSVersion</key>
                <string>9.0</string>
                <key>UILaunchImageName</key>
                <string>Default</string>
                <key>UILaunchImageOrientation</key>
                <string>Portrait</string>
                <key>UILaunchImageSize</key>
                <string>{320, 480}</string>
            </dict>
            <dict>
                <key>UILaunchImageMinimumOSVersion</key>
                <string>9.0</string>
                <key>UILaunchImageName</key>
                <string>Default-568h</string>
                <key>UILaunchImageOrientation</key>
                <string>Portrait</string>
                <key>UILaunchImageSize</key>
                <string>{320, 568}</string>
            </dict>
            <dict>
                <key>UILaunchImageMinimumOSVersion</key>
                <string>9.0</string>
                <key>UILaunchImageName</key>
                <string>Default-iPhone6</string>
                <key>UILaunchImageOrientation</key>
                <string>Portrait</string>
                <key>UILaunchImageSize</key>
                <string>{375, 667}</string>
            </dict>
            <dict>
                <key>UILaunchImageMinimumOSVersion</key>
                <string>9.0</string>
                <key>UILaunchImageName</key>
                <string>Default-iPhone6Plus</string>
                <key>UILaunchImageOrientation</key>
                <string>Portrait</string>
                <key>UILaunchImageSize</key>
                <string>{414, 736}</string>
            </dict>
            <dict>
                <key>UILaunchImageMinimumOSVersion</key>
                <string>9.0</string>
                <key>UILaunchImageName</key>
                <string>Default-1242h</string>
                <key>UILaunchImageOrientation</key>
                <string>Portrait</string>
                <key>UILaunchImageSize</key>
                <string>{414, 896}</string>
            </dict>
            <dict>
                <key>UILaunchImageMinimumOSVersion</key>
                <string>9.0</string>
                <key>UILaunchImageName</key>
                <string>Default-828h</string>
                <key>UILaunchImageOrientation</key>
                <string>Portrait</string>
                <key>UILaunchImageSize</key>
                <string>{414, 896}</string>
            </dict>
            <dict>
                <key>UILaunchImageMinimumOSVersion</key>
                <string>9.0</string>
                <key>UILaunchImageName</key>
                <string>Default-812h</string>
                <key>UILaunchImageOrientation</key>
                <string>Portrait</string>
                <key>UILaunchImageSize</key>
                <string>{375, 812}</string>
            </dict>
        </array>
        <key>UILaunchImages~ipad</key>
        <array>
            <dict>
                <key>UILaunchImageMinimumOSVersion</key>
                <string>7.0</string>
                <key>UILaunchImageName</key>
                <string>Default~ipad</string>
                <key>UILaunchImageOrientation</key>
                <string>Portrait</string>
                <key>UILaunchImageSize</key>
                <string>{768, 1024}</string>
            </dict>
            <dict>
                <key>UILaunchImageMinimumOSVersion</key>
                <string>9.0</string>
                <key>UILaunchImageName</key>
                <string>Default~ipad-1112h</string>
                <key>UILaunchImageOrientation</key>
                <string>Portrait</string>
                <key>UILaunchImageSize</key>
                <string>{834, 1112}</string>
            </dict>
            <dict>
                <key>UILaunchImageMinimumOSVersion</key>
                <string>9.0</string>
                <key>UILaunchImageName</key>
                <string>Default~ipad-1194h</string>
                <key>UILaunchImageOrientation</key>
                <string>Portrait</string>
                <key>UILaunchImageSize</key>
                <string>{834, 1194}</string>
            </dict>
            <dict>
                <key>UILaunchImageMinimumOSVersion</key>
                <string>9.0</string>
                <key>UILaunchImageName</key>
                <string>Default~ipad-1366h</string>
                <key>UILaunchImageOrientation</key>
                <string>Portrait</string>
                <key>UILaunchImageSize</key>
                <string>{1024, 1366}</string>
            </dict>
        </array>

#### 准备启动图

将启动图放在项目的根目录下，图片的名字如下

+ Default-1242h@3x.png	
+ Default-iPhone6.png	
+ Default~ipad-1194h.png
+ Default-568h.png	
+ Default-iPhone6Plus.png	
+ Default~ipad-1366h.png
+ Default-812h@3x.png	
+ Default.png		
+ Default~ipad.png
+ Default-828h@2x.png	
+ Default~ipad-1112h.png	
+ Default~ipad@2x.png

> **NOTE**:启动图对应的名字不能修改，否则不能生效

#### 启动图对应尺寸

启动图对应的尺寸如下，你可以找你们公司的UED设计

|启动图  | 尺寸  | 
|:-------------:|:-------------:| 
Default-1242h@3x.png	  | 1242 × 2688  | 
Default-iPhone6.png	  | 750 × 1334  | 
Default~ipad-1194h.png   | 834 × 1194  | 
Default-568h.png  | 	640 × 1136  | 
Default-iPhone6Plus.png	  | 1242 × 2208  | 
Default~ipad-1366h.png   | 640 × 960  | 
Default-812h@3x.png	  | 1125 × 2436  | 
Default.png	  | 640 × 960  | 
Default~ipad.png   | 768 × 1024  | 
Default-828h@2x.png	  | 828 × 1792  | 
Default~ipad-1112h.png	  | 834 × 1112  | 
Default~ipad@2x.png   | 1536 × 2048  | 

#### 检查并运行你的项目

如果你觉得这篇文章能帮助你解决问题，请给我[star](https://github.com/zhaoyuyu/CodePoets/)!!!
