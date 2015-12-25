# 一个良好划分Activity创建步骤的BaseActivity

> @author ASCE1885的 [Github](https://github.com/ASCE1885)  [简书](http://www.jianshu.com/users/4ef984470da8/latest_articles) [微博](http://weibo.com/asce885/profile?rightmod=1&wvr=6&mod=personinfo) [CSDN](http://blog.csdn.net/asce1885) [知乎](https://www.zhihu.com/people/asce1885)

一个Activity的创建过程其实包含几个不同的步骤，基本上都是在onCreate函数中完成的，这些步骤主要有：

* 设置页面的布局文件
* 初始化页面包含的控件
* 设置页面控件的点击响应事件
* 处理页面的业务逻辑

为了规范Activity的创建过程，我们有必要来创建一个模版，基于模版方法实现一个Activity的基类BaseActivity：

```java
/**
 * Activity基类，用于封装公共操作
 *
 * @author asce1885
 * @version 1.0.0
 * @date 2015.11.25
 */
public abstract class BaseActivity extends FragmentActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // 设置layout布局
        setContentView(initPageLayoutID());

        // 初始化页面控件
        initPageView();

        // 初始化页面控件点击
        initPageViewListener();

        // 业务逻辑处理
        processBusiness(savedInstanceState);
    }

    /**
     * 生成主文件布局ID
     */
    protected abstract int initPageLayoutID();
    
    /**
     * 初始化页面控件
     */
    protected abstract void initPageView();
    
    /**
     * 页面控件点击事件处理
     */
    protected abstract void initPageViewListener();
    
    /**
     * 业务逻辑处理
     *
     * @param savedInstanceState
     */
    protected abstract void processBusiness(Bundle savedInstanceState);

}
```
