# javascript-touch
javascript touch mobile

![GitHub language count](https://img.shields.io/github/languages/count/{username}/{repo-name})
![GitHub all releases](https://img.shields.io/github/downloads/{username}/{repo-name}/total)

## Mobile-Touch

 + Sizlere javascript içindeki touch eventlerin ne kadar basit ve geliştirebilir olduğunu göstericem.
  
  Touch Eventleri;
  1) <code>touchstart</code>, dokunmakla etkinleşen event listesidir.
  2) <code>touchend</code>, dokunan parmağın artık dokunmaması durumunda etkinleşen event listesidir.
  3) <code>touchmove</code>, dokunan parmağın temas eden her noktası için etkinleşen event listesidir.

  Touch Komutları;
  1) <code>touches</code>, Geçerli nesnedeki tüm temas noktalarının listesidir.
  2) <code>targetTouches</code>, Temas noktaları aynı düğümde başlayan noktalarının listesidir.
  3) <code>changedTouches</code>, Bir olayı tetiklerken değişen temas noktalarının listesidir.
  
  Diğer Komutlar;
  >1) <code>ctrlKey</code>, 'Ctrl' tuşuna basılıp basılmadığını gösterir.
  >2) <code>shiftKey</code>, 'shift' tuşuna basılıp basılmadığını gösterir.
  >3) <code>altKey</code>, 'alt' tuşuna basılıp basılmadığını gösterir.
  >4) <code>metaKey</code>, 'meta' tuşuna basılıp basılmadığını gösterir.
  ---
  style;
  
    #touch {
        font-size: 40px;
        height: 500px;
        width: 100%;
        border: 2px solid #000;
    }
    
  Html;
  
    <div id="touch"></div>

#### 1) touchstart & touchend 
    ---
    const touch = document.getElementById('touch')

    touch.addEventListener('touchstart', e => {
        // touch e started
        touch.innerHTML = "touch start";
        return ;
    })

    touch.addEventListener('touchend', e => {
        // touch e end
        touch.innerHTML = "touch end";
        return ;
    })  
    
   - Border içindeki alana dokunduğumuzda fonksiyon çalışır, dokunmayı bıraktığımızda fonksiyon tekrar çalışır.
   - Kullanımı gayet basit çalıştırmak istediklerinizi ve sonlanmasını istediğiniz fonksiyonları ve etkileşimleri eventlerin içine yazmanız yeterlidir.
   - Mobil ekranın her yerinde bu eventi çalıştırmak istiyorsanız, <code>touch.addEventListener</code> içindeki <code>touch</code> ifadesi yerine <code>document</code> yada <code>window</code> yazmak yeterli olucaktır.

#### 2) touchmove
  ---
    const touch = document.getElementById('touch')

    touch.addEventListener('touchmove', e => {
        // touch event started
        var x = e.touches[0].clientX;
        var y = e.touches[0].clientY;

        //console.log(x,y);
        touch.innerHTML = "clienty: "+x+ "<br>" +"clienty: "+y;
    })
    
   - Burada önemli olan <code>e.touches[0]</code> listedeki tek eleman olmasıdır. Bu yüzden index 0 almak zorunludur.
   - Event border içine dokunduğumuz anda başlar ve her hareketinizde fonksiyon sürekli olarak tekrarlar.
   - Mobil ekranın her yerinde bu eventi çalıştırmak istiyorsanız, <code>touch.addEventListener</code> içindeki <code>touch</code> ifadesi yerine <code>document</code> yada <code>window</code> yazmak yeterli olucaktır.
  
#### 3) touchswip
---
    const touch = document.getElementById('touch')
    let touchstartX = 0
    let touchendX = 0

    touch.addEventListener('touchstart', e => {
        touchstartX = e.changedTouches[0].clientX
        touchstartY = e.changedTouches[0].clientY

        console.log(e.changedTouches[0].clientX);
    })

    touch.addEventListener('touchend', e => {
        touchendX = e.changedTouches[0].clientX
        touchendY = e.changedTouches[0].clientY

        console.log(e.changedTouches[0].clientX);
        infoSwip()
    })

    function infoSwip() {
        if (touchstartX > touchendX && touchstartY > touchendY){
            touch.innerHTML = "swiped left, up"
        } else if (touchstartX > touchendX && touchendY > touchstartY) {
            touch.innerHTML = "swiped left, down"
        }
        if (touchendX > touchstartX && touchstartY > touchendY) {
            touch.innerHTML = "swiped right, up"
        } else if (touchendX > touchstartX && touchendY > touchstartY) {
            touch.innerHTML = "swiped right, down"
        }
    }
   
   - Kaydırma eventi için yazılmış basit kod bloğu için <code>e.changedTouches[0]</code> farklı parmak dokunuşlarınıda listeler. Burada kullanmamızın sebebi 'touchstart' ve 'touchend' eventleri için doğru sonuçları vermesi içindir. 
   - Yukarıdaki kod bloğunda tek yaptığımız kaydırma yönünü teyit etmektir. Bunun için <code>infoSwip()</code> fonksiyonuna bir kaç koşul eklememiz yeterlidir.
   - Mobil ekranın her yerinde bu eventi çalıştırmak istiyorsanız, <code>touch.addEventListener</code> içindeki <code>touch</code> ifadesi yerine <code>document</code> yada <code>window</code> yazmak yeterli olucaktır.
   
   


```diff
- text in red
+ text in green
! text in orange
+ asd
# text in gray
@@ text in purple (and bold)@@
```
