---
layout: post
title: UIViewAnimation
description: "弹簧、翻转、淡出淡入、翻页"
tags: [UIview],[Animation],[动画]
image:
  background: body_bg.gif
comments: true
share: true
---

<strong>UIView Animation</strong>其实已经提供了丰富的动画开发接口，除了基本的frame层面的动画，本文仅介绍弹簧、翻转、翻页、淡出淡入这几个，后续再继续加入其他动画。
 

###1.弹簧效果
[UIView animateWithDuration:0.8f delay:0.3 usingSpringWithDamping:0.6 initialSpringVelocity:0 options:UIViewAnimationOptionCurveLinear animations:^{
_imgView.center = self.view.center;
} completion:^(BOOL finished) {

}];
参数:
duration:动画时长
delay:延迟时间
damping:衰减率
velocity:初始速度
options:UIViewAnimationOptionCurveLinear       --  线性
        UIViewAnimationOptionCurveEaseInOut    --  先加速再减速        
        UIViewAnimationOptionCurveEaseIn       --  加速       
        UIViewAnimationOptionCurveEaseOut      --  减速
###2.淡出淡入
UIViewAnimationOptionTransitionCrossDissolve
[UIView transitionWithView:_imgView duration:1.0f options:UIViewAnimationOptionTransitionCrossDissolve animations:^{
    [weak_self flip];
} completion:^(BOOL finished) {

}];

###3.翻转
UIViewAnimationOptionTransitionFlipFromLeft/Right/Top/Bottom
-- from后面加翻转方向
[UIView transitionWithView:_imgView duration:1.0f options:UIViewAnimationOptionTransitionFlipFromLeft animations:^{
    [weak_self flip];
} completion:^(BOOL finished) {

}];

###4.翻页
UIViewAnimationOptionTransitionCurlUp/Down
-- 由上/下翻
[UIView transitionWithView:_imgView duration:1.0f options:UIViewAnimationOptionTransitionCurlUp animations:^{
    [weak_self flip];
} completion:^(BOOL finished) {

}];

- (void)flip
{
if (!_isFlipped) {
_imgView.image = [UIImage imageNamed:@"02动态.png"];
_isFlipped = YES;
}else{
_imgView.image = [UIImage imageNamed:@"02.png"];
_isFlipped = NO;
}
}

附上demo: <a href="https://github.com/jigeDevin/LZJViewAnimation" target="_blank" rel="nofollow">LZJViewAnimation</a>

