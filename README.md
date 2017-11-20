没什么内容，就是ionic2 官方的类有问题：


$ ionic cordova plugin add cordova-plugin-advanced-http

$ npm install --save @ionic-native/http

通过上述命令引入http插件后，无法正常使用，提示插件不可用。通过排查，
@ionic-native/http里面的名称写错了,index.js文件：

 …………
 
 HTTP = __decorate([
        Plugin({
            pluginName: 'HTTP',
            plugin: 'cordova-plugin-advanced-http',
            pluginRef: 'cordova.plugin.http',   <--------- 这里写错了
           repo: 'https://github.com/silkimen/cordova-plugin-advanced-http',
            platforms: ['Android', 'iOS']
        })
    ], HTTP);
    
    
…………


修改完名称，就好了：


 HTTP = __decorate([
        Plugin({
            pluginName: 'HTTP',
            plugin: 'cordova-plugin-advanced-http',
            pluginRef: 'cordovaHTTP', 
            repo: 'https://github.com/silkimen/cordova-plugin-advanced-http',
            platforms: ['Android', 'iOS']
        })
    ], HTTP);
    
    
 

