# XUI-REVERSE-PROXY

-----

### Прокси с использованием протоколов Trojan и VLESS (Reality) за реверс-прокси NGINX
Этот скрипт предназначен для быстрой и простой настройки скрытого прокси-сервера, использующего протоколы Trojan TLS и VLESS (Reality), с маскировкой через NGINX. В данном варианте все входящие запросы обрабатываются NGINX, а сервер работает как прокси-сервер только при условии, что запрос содержит правильный путь (URI). Это повышает безопасность и помогает скрыть истинное назначение сервера.

> [!IMPORTANT]
> Этот скрипт был протестирован на Debian 12 в среде виртуализации KVM. Для корректной работы вам потребуется собственный домен, который необходимо привязать к Cloudflare. Скрипт рекомендуется запускать с правами root на свежеустановленной системе.

Прежде чем запустить скрипт, рекомендуется выполнить следующие подготовительные действия:
1. Обновите систему и перезагрузите сервер.
2. Настройте Cloudflare:
   - Привяжите ваш домен к Cloudflare.
   - Добавьте следующие DNS записи:
| Type  | Name             | Content          | Proxy status  |
| ----- | ---------------- | ---------------- | ------------- |
| A     | your_domain_name | your_server_ip   | Proxied       |
| CNAME | www              | your_domain_name | DNS only      |
   
3. Настройки SSL/TLS в Cloudflare:
   - Перейдите в раздел SSL/TLS > Overview и выберите Full для параметра Configure.
   - Установите Minimum TLS Version на TLS 1.3.
   - Включите TLS 1.3 (true) в разделе Edge Certificates.

> [!NOTE]
> Скрипт настроен с учётом специфики маршрутизации для пользователей из России.

### Включает:
1) Настройку сервера 3X-UI Xray (протоколы Trojan Tls и VLESS Reality, подписка, json подписка)
2) Настройку обратного прокси NGINX на 443 порту
3) Настройку безопасности, включая автоматические обновления (unattended-upgrades)
4) SSL сертификаты Cloudflare с автоматическим обновлением
5) WARP
6) Включение BBR
7) Настройка UFW
8) Настройка SSH за NGINX
9) Отключение IPv6
10) Шифрование DNS запросов systemd-resolved или adguard-home (DNS over TLS или DNS over HTTPS) 

-----

### Использование:

Для настройки сервера выполните следующую команду:

```
bash <(curl -Ls https://github.com/cortez24rus/xui-reverse-proxy/raw/refs/heads/main/xui-rp-install.sh)
```

Затем введите необходимую информацию:

![image](https://github.com/user-attachments/assets/dc60caee-1b01-40c9-a344-e0a67ebfc2ee)

[!IMPORTANT] Скрипт предоставит все необходимые ссылки и данные для входа в административную панель XUI, а также другие важные данные для дальнейшей работы.
