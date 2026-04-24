# WebRTC Sunucusuz Chat

Sunucusuz, P2P mesajlaşma. İki cihaz karekod tarayarak bağlanır — mesajlar doğrudan cihazlar arasında gider.

**ŞİMDİ DENE:** https://theomgdev.github.io/WebRTC-Sunucusuz-Chat/

## Nasıl çalışır?

WebRTC bağlantısı kurulmadan önce iki tarafın birbirine bağlantı parametrelerini (SDP + ICE adayları) iletmesi gerekir. Bu uygulama bunu karekodla yapar:

1. **Başlatıcı** → offer oluşturur, QR gösterir
2. **Katılımcı** → QR'ı tarar, answer oluşturur, QR gösterir
3. **Başlatıcı** → cevap QR'ı tarar → P2P bağlantı kurulur

Bağlantı kurulduktan sonra mesajlar WebRTC DataChannel üzerinden akar, hiçbir sunucudan geçmez.

## Kullanım

### GitHub Pages

`index.html` dosyasını bir GitHub reposuna koy, Pages'i etkinleştir. HTTPS zorunlu olduğundan kamera doğrudan çalışır.

### Yerel test

```
npx serve .
```

veya herhangi bir static file server. `file://` üzerinden kamera açılmaz (tarayıcı kısıtlaması).

## NAT geçişi

| Durum | Yöntem |
|---|---|
| Aynı ağ | Direkt (LAN) |
| Farklı ağ, normal NAT | STUN (Google + Cloudflare) |
| Simetrik NAT (nadir) | TURN relay (Open Relay Project) |

Bağlandıktan sonra header'da hangi yöntemin seçildiği gösterilir.
