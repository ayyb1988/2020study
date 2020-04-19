######1.1 使用说明
```
下面两套方案实现的效果不同

skinNormalColor = SkinResourcesUtils.getInstance().getColor(SkinColorType.BASIC_WIDGET)
mNormalColorFilter = SkinResourcesUtils.getInstance().color2ColorFilter(skinNormalColor);
drawable.mutate().setColorFilter(mNormalColorFilter);

或者
int skinNormalColor = SkinResourcesUtils.getInstance().getColor(SkinColorType.BASIC_WIDGET);
drawable.mutate().setColorFilter(skinNormalColor, PorterDuff.Mode.SRC_ATOP);

```
######1.2 关键类 
SkinFactory
SkinEngine
AttrUtils
SkinResourcesUtils
SkinColorSrcAttr
SkinColorType

######1.3 实现框架
######1.4 代码分析
######1.5 相关技术


##### 二. 网络资源
[Android QQ技术分享三(QQ换肤之SkinEngine实现)  ](http://download.csdn.net/detail/cc_want/9187187#comment)
[Android 源码系列之<四>从源码的角度深入理解LayoutInflater.Factory之主题切换(上)(中)(下)](http://blog.csdn.net/llew2011/article/details/51252401)

