Systemd-resolved
=========

Setup systemd-resolved service


Role Variables
--------------

DNS: Список IP-адресов DNS-серверов, которые systemd-resolved использует в качестве основных серверов для разрешения имен.

FallbackDNS: Список IP-адресов резервных DNS-серверов, используемых systemd-resolved, если основные DNS-серверы недоступны или не отвечают.

Domains: Список доменов, для которых systemd-resolved будет использовать особые правила разрешения имен.

DNSSEC: Определяет, должен ли systemd-resolved использовать DNSSEC для проверки подлинности ответов DNS.

DNSOverTLS: Указывает, должен ли systemd-resolved использовать TLS для шифрования запросов DNS к DNS-серверам, поддерживающим DNS-over-TLS, для повышения конфиденциальности и безопасности.

MulticastDNS: Включает или отключает поддержку Multicast DNS (mDNS).

LLMNR: Включает или отключает поддержку Link-Local Multicast Name Resolution (LLMNR).

Cache: Управляет кэшированием ответов DNS systemd-resolved.

DNSStubListener: Управляет слушателем "перехватчика" DNS в systemd-resolved, который слушает на адресе 127.0.0.53 и предоставляет совместимость с традиционными программами, ожидающими, что DNS-сервер будет доступен на локальном адресе.


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```
---
- name: Install dante-server
  hosts: client-dns
  roles:
    - ansible-systemd-resolved
  vars:
    settings:
      - key: "DNS"
        value: "192.168.16.101 192.168.16.102 8.8.8.8"
      - key: "FallbackDNS"
        value: "192.168.16.100 1.1.1.1"
      - key: "Domains"
        value: "example.com"
      - key: "DNSSEC"
        value: "no"
      - key: "DNSOverTLS"
        value: "no"
      - key: "MulticastDNS"
        value: "no"
      - key: "LLMNR"
        value: "no"
      - key: "Cache"
        value: "yes"
      - key: "DNSStubListener"
        value: "no"
```

License
-------

Apache-2.0

Author Information
------------------

Alexey
