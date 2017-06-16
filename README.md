## fork后更新说明
- 20170616 添加自定义PageIndicator距离边界

[![Android Gems](http://www.android-gems.com/badge/saiwu-bigkoo/Android-ConvenientBanner.svg?branch=master)](http://www.android-gems.com/lib/saiwu-bigkoo/Android-ConvenientBanner)

### config in java code

```java
//自定义你的Holder，实现更多复杂的界面，不一定是图片翻页，其他任何控件翻页亦可。
convenientBanner.setPages(
                new CBViewHolderCreator<LocalImageHolderView>() {
                    @Override
                    public LocalImageHolderView createHolder() {
                        return new LocalImageHolderView();
                    }
                }, localImages)
                //设置两个点图片作为翻页指示器，不设置则没有指示器，可以根据自己需求自行配合自己的指示器,不需要圆点指示器可用不设
                .setPageIndicator(new int[]{R.drawable.ic_page_indicator, R.drawable.ic_page_indicator_focused})
                //设置指示器的方向
                .setPageIndicatorAlign(ConvenientBanner.PageIndicatorAlign.ALIGN_PARENT_RIGHT)
                //设置翻页的效果，不需要翻页效果可用不设
                //.setPageTransformer(Transformer.DefaultTransformer);    集成特效之后会有白屏现象，新版已经分离，如果要集成特效的例子可以看Demo的点击响应。
//        convenientBanner.setManualPageable(false);//设置不能手动影响

public class LocalImageHolderView implements Holder<Integer>{
    private ImageView imageView;
    @Override
    public View createView(Context context) {
        imageView = new ImageView(context);
        imageView.setScaleType(ImageView.ScaleType.FIT_XY);
        return imageView;
    }

    @Override
    public void UpdateUI(Context context, final int position, Integer data) {
        imageView.setImageResource(data);
    }
}
```

## Thanks

- [ViewPagerTransforms](https://github.com/ToxicBakery/ViewPagerTransforms)
- [salvage](https://github.com/JakeWharton/salvage)
- [LoopingViewPager](https://github.com/imbryk/LoopingViewPager)

>## 更新说明
>v1.1.0 修复了往前滑动最后一页会变空白页的BUG  <br />
>v1.1.1 修复第三方图库下载setTag出错的BUG  <br />

>v1.1.2
 - 修复下拉刷新自动翻页偶尔失效停止BUG  <br />
 - 提供onPageChangeListener的API调用  <br />
 
>v1.1.3
 - 循环控制，可以设置为不循环模式  <br />
 - 加入OnItemClcikListener监听器，修复原先点击图片position失准BUG  <br />
 - 调整notifyDataSetChanged函数，并加入notifyDataSetAdd函数  <br />

>v1.1.4
 - getCurrentPageIndex函数改为getCurrentItem  <br />
 - 加入setcurrentitem函数  <br />

>v2.0.0
 - 重新修改循环逻辑  <br />
 - 解决卡顿和白屏现象  <br />
 - Demo中加入下拉刷新和控件左右拨动冲突方案  <br />
 
>v2.0.1
 - 回滚到1.1.4的循环逻辑  <br />
 - 分离特效代码  <br />

>v2.0.2
 - 调整setOnItemClickListener  <br />
 - 加入代码New 控件和 add ListView的HeaderView效果例子  <br />
 
>v2.0.3
 - 逻辑由  301230 改为 012301230123—》当第一个0的时候变为第二个0，最后一个3的时候变为第二个3 <br />
 
>v2.0.4
 - 修复添加动画效果后点击无效问题 <br />

>v2.0.5
 - 使用WeakReference fix 内存泄漏问题 <br />
