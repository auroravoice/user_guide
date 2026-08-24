---
title: Auroravoice · English
---

[Intro](index.md) · [Install](install.md) · [Guide](guide.md) · [Voices & Models](voices.md) · [FAQ](faq.md) · [Privacy](privacy.md) | **[简体中文](../zh/index.md)**


*"The house was quiet and the world was calm. The reader became the book…"*

Auroravoice is a local desktop app for macOS that reads Chinese (and English) text files aloud with natural, human-like voices — fully offline, powered by on-device MLX inference.

<div class="hero-carousel" data-carousel>
  <div class="carousel-viewport">
    <div class="carousel-track">
      <div class="carousel-slide">
        <div class="card">
          <img class="lightbox-trigger" src="../pics/En_splashscreen.png" alt="Auroravoice splash screen" />
          <div class="cap">Splash screen · click to enlarge</div>
        </div>
      </div>
      <div class="carousel-slide">
        <div class="card">
          <img class="lightbox-trigger" src="../pics/screenshot_english_reading.png" alt="English reading interface" />
          <div class="cap">English reading interface · click to enlarge</div>
        </div>
      </div>
      <div class="carousel-slide">
        <div class="card">
          <img class="lightbox-trigger" src="../pics/screenshot_record_reference_voice.png" alt="Recording reference voice" />
          <div class="cap">Recording reference voice · click to enlarge</div>
        </div>
      </div>
      <div class="carousel-slide">
        <div class="card">
          <img class="lightbox-trigger" src="../pics/screenshot_chinese_reading.png" alt="Chinese reading interface" />
          <div class="cap">Chinese reading interface · click to enlarge</div>
        </div>
      </div>
      <div class="carousel-slide">
        <div class="card">
          <div class="video-thumb" data-vid="qzCEzKN36EU">
            <img src="../pics/video_poster.png" alt="Demo video cover" onerror="this.onerror=null;this.src='https://img.youtube.com/vi/qzCEzKN36EU/maxresdefault.jpg';" />
            <span class="play" aria-label="Play demo video"></span>
          </div>
          <div class="cap">Demo video · click to play</div>
        </div>
      </div>
    </div>
  </div>
  <button class="carousel-btn prev" aria-label="Previous">‹</button>
  <button class="carousel-btn next" aria-label="Next">›</button>
  <div class="carousel-dots" aria-label="Carousel indicators"></div>
  <div class="carousel-hint">← Swipe to cycle · click image to enlarge / video to play →</div>
</div>

<div id="av-lightbox" class="av-lightbox" role="dialog" aria-modal="true" aria-label="Image preview">
  <button class="close" aria-label="Close">×</button>
  <img alt="preview" />
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
      d.setAttribute('aria-label','Slide '+(i+1));
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

## Highlights

- **Local inference** — models run on your Apple Silicon Mac; your text never leaves the machine
- **Listen while generating** — chunk-by-chunk synthesis, playback starts immediately
- **Voice cloning** — read a sample in-app or import audio; a personal voice in under a minute
- **Resume anywhere** — progress auto-saved every few seconds; synthesis picks up where it stopped
- **Multi-engine** — local MLX (recommended), remote API, or Edge TTS
- **Bilingual UI** — 中文 / English, 5 preset themes

## Who it's for

- Anyone who'd rather *listen* to novels and articles
- Privacy-conscious users who want TTS fully offline
- People who want text read in their own voice

> 💬 Have ideas or issues? [Submit feedback & suggestions →](https://github.com/auroravoice/user_guide/issues/new?template=feedback.yml)

Next: [Installation →](install.md)
