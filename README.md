简单可信赖的分享视图,直接拿来用
===

##使用FYShareView
- - -
###效果图
![](https://raw.githubusercontent.com/wufeiyue/FYShareView/master/Resources/show.png)  
###使用CocoaPods导入FYShareView
在`Podfile`中进行如下导入：
```
pod 'FYShareView'
```
然后使用`cocoaPods`进行安装  
###第二步：遵守FYShareViewDelegate协议，并在初始化方式中指定为自己
```

class ViewController: UIViewController {
	func setupShareView() {
        let friend = FYShareItemModel(title: "朋友圈", normal: "share_friend", highlighted: "share_friend_hover", id: "friend")
        let qq = FYShareItemModel(title: "QQ", normal: "share_qq", highlighted: "share_qq_hover", id: "qq")
        let sina = FYShareItemModel(title: "微博", normal: "share_sina", highlighted: "share_sina_hover", id: "sina")
        let wechat = FYShareItemModel(title: "微信", normal: "share_weixin", highlighted: "share_weixin_hover", id: "wechat")
        let qzone = FYShareItemModel(title: "QQ空间", normal: "share_zone", highlighted: "share_zone_hover", id: "qzone")
        
        shareView = FYShareView(frame: view.bounds, items:  [wechat, friend, sina, qq, qzone])
        shareView.delegate = self
        view.addSubview(shareView)
    }
    
    @objc func btnDidTapped() {
		    //调用展示视图
        shareView.show()
    }
}

extension ViewController: FYShareViewDelegate {
    func shareView(itemDidTapped identifier: String) {
        print("identifier:\(identifier)")
    }
}
```
###说明
![](https://raw.githubusercontent.com/wufeiyue/FYShareView/master/Resources/specification.png)
```
var style = FYShareStyle()
style.insetHorizontal = 10
style.cancelHeight = 42
shareView.style = style
```  
**版本更新：**
- 1.0.1 提交基础展示UI视图
> 有任何疑问，欢迎留言讨论及分享