# javascript-touch
javascript touch mobile

## Mobile-Touch

  Sizlere javascript içindeki touch eventlerin ne kadar basit ve geliştirebilir olduğunu göstericem.

  1) touchstart & touchend 
    
    const touch = document.getElementById('touch')

    touch.addEventListener('touchstart', event => {
        // touch event started
        touch.innerHTML = "touch start";
        return ;
    })

    touch.addEventListener('touchend', event => {
        // touch event end
        touch.innerHTML = "touch end";
        return ;
    })  
    
   - Border içindeki alana dokunduğumuzda fonksiyon çalışır, dokunmayı bıraktığımızda fonksiyon tekrar çalışır.
   - Kullanımı gayet basit çalıştırmak istediklerinizi ve sonlanmasını istediğiniz fonksiyonları ve etkileşimleri eventlerin içine yazmanız yeterlidir.
   - Mobil ekranın her yerinde bu eventi çalıştırmak istiyorsanız, 'touch.addEventListener' içindeki 'touch' ifadesi yerine 'document' yada 'window' yazmak yeterli olucaktır.

  2) touchmove
  
    const touch = document.getElementById('touch')

    touch.addEventListener('touchmove', event => {
        // touch event started
        var x = event.touches[0].clientX;
        var y = event.touches[0].clientY;

        //console.log(x,y);
        touch.innerHTML = "clienty: "+x+ "<br>" +"clienty: "+y;
    })
    
   - Event border içine dokunduğumuz anda başlar ve her hareketinizde fonksiyon sürekli olarak tekrarlar.
   - Mobil ekranın her yerinde bu eventi çalıştırmak istiyorsanız 'touch' ifadesi yerine 'document' yada 'window' yazmak yeterli olucaktır.
   
   
