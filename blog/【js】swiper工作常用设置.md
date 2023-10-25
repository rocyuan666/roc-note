## swiper轮播图，工作常用设置总结
```css
<div class="swiper-container">
  <div class="swiper-wrapper">
      <div class="swiper-slide"><img src="//game.gtimg.cn/images/yrzx/cp/a20200308qhhdm/game-screenshot-5.jpg" alt="" width="670" height="376"></div>
      <div class="swiper-slide"><img src="//game.gtimg.cn/images/yrzx/cp/a20200308qhhdm/game-screenshot-4.jpg" alt="" width="670" height="376"></div>
      <div class="swiper-slide"><img src="//game.gtimg.cn/images/yrzx/cp/a20200308qhhdm/game-screenshot-3.jpg" alt="" width="670" height="376"></div>
      <div class="swiper-slide"><img src="//game.gtimg.cn/images/yrzx/cp/a20200308qhhdm/game-screenshot-1.jpg" alt="" width="670" height="376"></div>
      <div class="swiper-slide"><img src="//game.gtimg.cn/images/yrzx/cp/a20200308qhhdm/game-screenshot-2.jpg" alt="" width="670" height="376"></div>
  </div>
  <!-- Add Pagination -->
  <div class="swi-pagination"></div>
  <!-- Add Arrows -->
  <div class="spr swiper-button-prev"></div>
  <div class="spr swiper-button-next"></div>
</div>

<script src="//ossweb-img.qq.com/images/js/swiper4_component/js/swiper.min.js"></script>

// swiper常用初始化
var swiper = new Swiper('.swiper-container', {
  autoplay: {
    // 用户手碰到轮播图不停止
    disableOnInteraction: false
  },
  // 分页class设置
  pagination: {
    el: '.swi-pagination',
    bulletClass: 'swi-bullet',
    bulletActiveClass: 'swi-active-bullet'
  },
  // 左右按钮class设置
  navigation: {
    prevEl: '.swiper-button-prev',
    nextEl: '.swiper-button-next'
  },
  on:{
    // 用户滑动滚动结束后，数据上报（腾讯互娱）
    transitionEnd: function(){
      var idx = swiper.activeIndex+1
      PTTSendClick('pop','banner'+idx,'游戏特色轮播图'+idx);
    },
  }
});
```
