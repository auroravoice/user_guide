---
title: 曦光聆 · 简体中文
---

[简介](index.md) · [安装](install.md) · [使用指南](guide.md) · [音色与模型](voices.md) · [FAQ](faq.md) · [隐私政策](privacy.md) · [更新日志](changelog.md) | **[English](../en/index.md)**


曦光聆是一款本地运行的桌面应用：打开一个书籍文件夹（内含 `.txt` 文本），应用会把文本智能分块，用自然真人语音逐段朗读——支持声音克隆、断点续读、语速调节。

<div class="hero-carousel" data-carousel>
  <div class="carousel-viewport">
    <div class="carousel-track">
      <div class="carousel-slide">
        <div class="card">
          <img class="lightbox-trigger" src="../pics/Zh_splashscreen.png" alt="曦光聆启动页" />
          <div class="cap">启动页 · 点击放大</div>
        </div>
      </div>
      <div class="carousel-slide">
        <div class="card">
          <img class="lightbox-trigger" src="../pics/screenshot_chinese_reading.png" alt="中文朗读界面" />
          <div class="cap">中文朗读界面 · 点击放大</div>
        </div>
      </div>
      <div class="carousel-slide">
        <div class="card">
          <img class="lightbox-trigger" src="../pics/screenshot_record_reference_voice.png" alt="录制参考音频" />
          <div class="cap">录制参考音频 · 点击放大</div>
        </div>
      </div>
      <div class="carousel-slide">
        <div class="card">
          <img class="lightbox-trigger" src="../pics/screenshot_english_reading.png" alt="英文朗读界面" />
          <div class="cap">英文朗读界面 · 点击放大</div>
        </div>
      </div>
      <div class="carousel-slide">
        <div class="card">
          <div class="video-thumb" data-vid="qzCEzKN36EU">
            <img src="../pics/video_poster.png" alt="演示视频封面" onerror="this.onerror=null;this.src='https://img.youtube.com/vi/qzCEzKN36EU/maxresdefault.jpg';" />
            <span class="play" aria-label="播放演示视频"></span>
          </div>
          <div class="cap">演示视频 · 点击播放</div>
        </div>
      </div>
    </div>
  </div>
  <button class="carousel-btn prev" aria-label="上一张">‹</button>
  <button class="carousel-btn next" aria-label="下一张">›</button>
  <div class="carousel-dots" aria-label="轮播指示"></div>
  <div class="carousel-hint">← 左右滑动循环切换 · 点击图片放大 / 视频播放 →</div>
</div>

<div id="av-lightbox" class="av-lightbox" role="dialog" aria-modal="true" aria-label="图片预览">
  <button class="close" aria-label="关闭">×</button>
  <img alt="预览图" />
</div>

<script>
(function(){
  document.querySelectorAll('.hero-carousel').forEach(function(carousel){
    var track = carousel.querySelector('.carousel-track');
    var slides = carousel.querySelectorAll('.carousel-slide');
    var dotsWrap = carousel.querySelector('.carousel-dots');
    var prevBtn = carousel.querySelector('.carousel-btn.prev');
    var nextBtn = carousel.querySelector('.carousel-btn.next');
    var n = slides.length, idx = 0;
    dotsWrap.innerHTML = '';
    for(var i=0;i<n;i++){
      var d=document.createElement('button');
      d.className='dot'+(i===0?' active':'');
      d.setAttribute('data-index', i);
      d.setAttribute('aria-label','第'+(i+1)+'张');
      dotsWrap.appendChild(d);
    }
    var dots = dotsWrap.querySelectorAll('.dot');
    function go(i){
      idx = (i+n)%n;
      track.style.transform='translateX('+(-idx*100)+'%)';
      dots.forEach(function(d,j){ d.classList.toggle('active', j===idx); });
    }
    prevBtn.addEventListener('click', function(){ go(idx-1); });
    nextBtn.addEventListener('click', function(){ go(idx+1); });
    dotsWrap.addEventListener('click', function(e){
      if(e.target.classList.contains('dot')) go(parseInt(e.target.getAttribute('data-index'),10));
    });
    var startX=0, dx=0, dragging=false;
    var viewport = carousel.querySelector('.carousel-viewport');
    function onStart(x){ startX=x; dx=0; dragging=true; track.style.transition='none'; }
    function onMove(x){ if(!dragging) return; dx=x-startX; track.style.transform='translateX(calc('+(-idx*100)+'% + '+dx+'px))'; }
    function onEnd(){
      if(!dragging) return; dragging=false; track.style.transition='';
      if(Math.abs(dx)>50){ if(dx<0) go(idx+1); else go(idx-1); } else go(idx);
    }
    viewport.addEventListener('touchstart', function(e){ onStart(e.touches[0].clientX); }, {passive:true});
    viewport.addEventListener('touchmove', function(e){ onMove(e.touches[0].clientX); }, {passive:true});
    viewport.addEventListener('touchend', onEnd);
    viewport.addEventListener('mousedown', function(e){ onStart(e.clientX); e.preventDefault(); });
    window.addEventListener('mousemove', onMove);
    window.addEventListener('mouseup', onEnd);
    viewport.addEventListener('mouseleave', function(){ if(dragging) onEnd(); });
    carousel.setAttribute('tabindex','0');
    carousel.addEventListener('keydown', function(e){ if(e.key==='ArrowLeft') go(idx-1); if(e.key==='ArrowRight') go(idx+1); });
    carousel.querySelectorAll('.lightbox-trigger').forEach(function(img){
      img.addEventListener('click', function(){
        var lb=document.getElementById('av-lightbox');
        if(!lb) return;
        var lbImg=lb.querySelector('img');
        lbImg.src=img.src; lbImg.alt=img.alt;
        lb.classList.add('open');
      });
    });
    carousel.querySelectorAll('.video-thumb').forEach(function(th){
      th.addEventListener('click', function(){
        var vid=th.getAttribute('data-vid');
        var wrap=document.createElement('div');
        wrap.className='video-wrap';
        wrap.innerHTML='<iframe src="https://www.youtube.com/embed/'+vid+'?autoplay=1&rel=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>';
        th.replaceWith(wrap);
      });
    });
  });
  var lb=document.getElementById('av-lightbox');
  if(lb){
    lb.addEventListener('click', function(e){ if(e.target===lb || e.target.classList.contains('close')) lb.classList.remove('open'); });
    document.addEventListener('keydown', function(e){ if(e.key==='Escape') lb.classList.remove('open'); });
  }
})();
</script>

## 核心特性

- 🖥️ **本地推理**：基于 MLX，模型跑在你自己的 Apple Silicon 芯片上，文本不上传
- 📖 **边生成边听**：逐块合成、即时播放，不用等整本书合成完
- 🎙️ **声音克隆**：在应用里朗读几十秒，或导入一段音频，即可创建专属音色
- 🔖 **断点续合**：已生成的段落直接复用，中断后从上次位置继续；播放未生成完的章节还会自动续生成
- 💾 **进度记忆**：按章节记忆阅读位置与书签，切章返回、重启后接着听
- ⚡ **多引擎**：本地 MLX（推荐）/ 远程 API / Edge TTS 三种引擎随时切换
- 🌐 **双语界面**：中文 / English 一键切换，5 个预设主题

## 适合谁

- 📚 想把小说、文章「听」完的人
- 🔒 在意隐私、希望语音合成完全离线的人
- 🎙️ 想要用自己的声音来朗读文字的人

> 💬 有想法或遇到问题？[点此提交反馈与建议 →](https://github.com/auroravoice/user_guide/issues/new?template=feedback.yml)

下一页：[安装与启动 →](install.md)
