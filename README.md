# bintray
处理上传bintray的gradle文件

## 根目录build.gradle中添加
```
    dependencies {
        ...
        // 下面两行是新添加的
        classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.8.4'
        classpath 'com.github.dcendents:android-maven-gradle-plugin:2.1'
    }
    
 allprojects {
    ...
    //解决上传jCenter乱码问题
    tasks.withType(Javadoc){
        options{
            encoding "UTF-8"
            charSet 'UTF-8'
            links "http://docs.oracle.com/javase/7/docs/api"
        }
    }
}   
    
```
## local.properties中添加
```
bintray.user=user
bintray.apikey=apikey
```
## lib中的build.gradle添加
```
ext {
    libraryPackaging = 'aar'                                            //上传aar形式的打包文件

    // jcenter
    bintrayRepo = "tgcity"                                             // 你上传的位于bintray中的Repository名称，如果没有创建会有一个叫maven的
    name = 'log'                                                // 必须和library module的名字相同
    libraryDesc = 'A log Library'
    publishedGroupId = 'com.tgcity.utils'                // 填写groupId， 一般是包名，比如：com.android.support
    versionName = '1.0.0'                                               // 版本号，比如：22.2.1
    websiteUrl = 'https://github.com/tgcityPlum/Comprehensive'              // 可以填写github上的库地址.
    issueTrackerUrl = 'https://github.com/tgcityPlum/Comprehensive/issues'  // 可以填写github库的issue地址.
    vcsUrl = 'https://github.com/tgcityPlum/Comprehensive.git'              // 可以填写github上库的地址.
    licenseName = "Apache-2.0"
    libraryVersionDesc = 'version descriotion'

}

apply from: 'https://github.com/tgcityPlum/bintray/blob/master/jcenter.gradle'
```
## 使用方法
windows环境在terminal中输入 gradlew jcenter 即可
