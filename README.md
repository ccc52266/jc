ipv6: true
allow-lan: true
mixed-port: 7890
unified-delay: false
tcp-concurrent: true
external-controller: 127.0.0.11:1111
external-ui: ui
external-ui-url: "https://yacd.metacubex.one/"
geodata-mode: true
geox-url:
  geoip: "https://mirror.ghproxy.com/https://github.com/MetaCubeX/meta-rules-dat/releases/download/latest/geoip-lite.dat"
  geosite: "https://mirror.ghproxy.com/https://github.com/MetaCubeX/meta-rules-dat/releases/download/latest/geosite.dat"
  mmdb: "https://mirror.ghproxy.com/https://github.com/MetaCubeX/meta-rules-dat/releases/download/latest/country-lite.mmdb"
global-client-fingerprint: chrome
dns:
  nameserver:
    - 119.29.29.29
    - 223.5.5.5
    - 223.6.6.6
  fallback:
    - 8.8.8.8
    - 8.8.4.4
    - tls://1.0.0.1:853
    - tls://dns.google:853
  listen: :1053
  ipv6: true
  enhanced-mode: fake-ip
  fake-ip-range: 198.18.0.1/16
  proxy-server-nameserver:
    - https://doh.pub/dns-query
  nameserver-policy:
    "geosite:cn,private":
      - "https://doh.pub/dns-query"
      - "https://dns.alidns.com/dns-query"
    "geosite:geolocation-!cn":
      - "https://dns.cloudflare.com/dns-query#dns"
      - "https://dns.google/dns-query#dns"
  default-nameserver:
     - 223.5.5.5
     - 223.6.6.6
  geoip: true
  geoip-code: CN
  
proxy-providers:
  Nexitally_Subscription: &Nexitally
    type: http
    url: "https://ilmmvs.lol/?L2Rvd25sb2FkQ29uZmlnL0NsYXNoLmFzcHg/ZXE9YW5kcm9pZCZ1cms9NGI1NWM0YzEtZDRjMi00MjUwLThmN2EtNGQ3YzUwOTMwZDE5Jm1tPTIyMjE5NyZiNTM4"
    interval: 1200
    path: ./providers/proxy/Nexitally.yaml
    health-check:
      enable: true
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204

  Kuromi_Subscription: &Kuromi
    type: http
    url: "https://v1.mk/agG4qIm"
    interval: 1200
    path: ./providers/proxy/Kuromi.yaml
    health-check:
      enable: true
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204


  Chinaairport_Subscription: &Chinaairport
    type: http
    url: "https://nachoneko.cn/api/v1/client/subscribe?token=76d849379e5e6182b4b8978fe0a1aa01"
    interval: 1200
    path: ./providers/proxy/Chinaairport.yaml
    health-check:
      enable: true
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204

#订阅正则提取分组
#Nexitally部分
  Nexitally_Filter_All:
    <<: *Nexitally
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset))

  Nexitally_Filter_HK:
    <<: *Nexitally
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(🇭🇰|香港|Hong|HK)

  Nexitally_Filter_TW:
    <<: *Nexitally
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(TW|🇹🇼|台湾|TaiWan|🇨🇳)

  Nexitally_Filter_SG:
    <<: *Nexitally
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(SG|新加坡|🇸🇬|Singapore)

  Nexitally_Filter_US:
    <<: *Nexitally
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(美国|States|American|USA|Seattle|San Jose|Los Angeles|🇺🇸)

  Nexitally_Filter_JP:
    <<: *Nexitally
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(日本|JP|Japan|🇯🇵)

  Nexitally_Filter_EU:
    <<: *Nexitally
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(德国|法国|荷兰|意大利|西班牙|土耳其|挪威|瑞士|瑞典|爱尔兰|芬兰|丹麦|波兰|匈牙利|英国|UK|比利时|卢森堡|希腊|葡萄牙|俄罗斯|爱尔兰|斯洛伐克|保加利亚|塞尔维亚|克罗地亚|奥地利|摩纳哥|立陶宛|拉脱维亚|罗马尼亚|捷克|乌克兰|Germany|France|Netherlands|Italy|Spain|Turkey|Norway|Switzerland|Sweden|Ireland|Finland|Denmark|Poland|Hungary|UnitedKingdom|UK|Belgium|Luxembourg|Greece|Portugal|Russia|Ireland|Slovakia|Bulgaria|Serbia|Croatia|Austria|Monaco|Lithuania|Latvia|Romania|Czech|Republic|Ukraine|🇩🇪|🇫🇷|🇳🇱|🇮🇹|🇪🇸|🇹🇷|🇳🇴|🇨🇭|🇸🇪|🇮🇪|🇫🇮|🇩🇰|🇵🇱|🇭🇺|🇧🇪|🇱🇺|🇬🇷|🇵🇹|🇦🇹|🇱🇹|🇱🇻|🇷🇴|🇨🇿|🌍|🇺🇦|🇬🇧|🇷🇺|🇮🇪|🇸🇰|🇧🇬|🇷🇸|🇭🇷|🇲🇨)


#Kuromi部分
  Kuromi_Filter_All:
    <<: *Kuromi
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset))

  Kuromi_Filter_HK:
    <<: *Kuromi
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(🇭🇰|香港|Hong|HK)

  Kuromi_Filter_TW:
    <<: *Kuromi
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(TW|🇹🇼|台湾|TaiWan|🇨🇳)

  Kuromi_Filter_SG:
    <<: *Kuromi
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(SG|新加坡|🇸🇬|Singapore)

  Kuromi_Filter_US:
    <<: *Kuromi
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(美国|States|American|USA|Seattle|San Jose|Los Angeles|🇺🇸)

  Kuromi_Filter_JP:
    <<: *Kuromi
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(日本|JP|Japan|🇯🇵)

  Kuromi_Filter_EU:
    <<: *Kuromi
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(德国|法国|荷兰|意大利|西班牙|土耳其|挪威|瑞士|瑞典|爱尔兰|芬兰|丹麦|波兰|匈牙利|英国|UK|比利时|卢森堡|希腊|葡萄牙|俄罗斯|爱尔兰|斯洛伐克|保加利亚|塞尔维亚|克罗地亚|奥地利|摩纳哥|立陶宛|拉脱维亚|罗马尼亚|捷克|乌克兰|Germany|France|Netherlands|Italy|Spain|Turkey|Norway|Switzerland|Sweden|Ireland|Finland|Denmark|Poland|Hungary|UnitedKingdom|UK|Belgium|Luxembourg|Greece|Portugal|Russia|Ireland|Slovakia|Bulgaria|Serbia|Croatia|Austria|Monaco|Lithuania|Latvia|Romania|Czech|Republic|Ukraine|🇩🇪|🇫🇷|🇳🇱|🇮🇹|🇪🇸|🇹🇷|🇳🇴|🇨🇭|🇸🇪|🇮🇪|🇫🇮|🇩🇰|🇵🇱|🇭🇺|🇧🇪|🇱🇺|🇬🇷|🇵🇹|🇦🇹|🇱🇹|🇱🇻|🇷🇴|🇨🇿|🌍|🇺🇦|🇬🇧|🇷🇺|🇮🇪|🇸🇰|🇧🇬|🇷🇸|🇭🇷|🇲🇨)

#Chinaairport部分
  Chinaairport_Filter_All:
    <<: *Chinaairport
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset))

  Chinaairport_Filter_HK:
    <<: *Chinaairport
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(🇭🇰|香港|Hong|HK)

  Chinaairport_Filter_TW:
    <<: *Chinaairport
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(TW|🇹🇼|台湾|TaiWan|🇨🇳)

  Chinaairport_Filter_SG:
    <<: *Chinaairport
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(SG|新加坡|🇸🇬|Singapore)

  Chinaairport_Filter_US:
    <<: *Chinaairport
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(美国|States|American|USA|Seattle|San Jose|Los Angeles|🇺🇸)

  Chinaairport_Filter_JP:
    <<: *Chinaairport
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(日本|JP|Japan|🇯🇵)

  Chinaairport_Filter_EU:
    <<: *Chinaairport
    filter: ^(?!.*(Days Left|国内|国际|工单|回国|官网|Premium|GB|Expire Date|Traffic Reset)).*(德国|法国|荷兰|意大利|西班牙|土耳其|挪威|瑞士|瑞典|爱尔兰|芬兰|丹麦|波兰|匈牙利|英国|UK|比利时|卢森堡|希腊|葡萄牙|俄罗斯|爱尔兰|斯洛伐克|保加利亚|塞尔维亚|克罗地亚|奥地利|摩纳哥|立陶宛|拉脱维亚|罗马尼亚|捷克|乌克兰|Germany|France|Netherlands|Italy|Spain|Turkey|Norway|Switzerland|Sweden|Ireland|Finland|Denmark|Poland|Hungary|UnitedKingdom|UK|Belgium|Luxembourg|Greece|Portugal|Russia|Ireland|Slovakia|Bulgaria|Serbia|Croatia|Austria|Monaco|Lithuania|Latvia|Romania|Czech|Republic|Ukraine|🇩🇪|🇫🇷|🇳🇱|🇮🇹|🇪🇸|🇹🇷|🇳🇴|🇨🇭|🇸🇪|🇮🇪|🇫🇮|🇩🇰|🇵🇱|🇭🇺|🇧🇪|🇱🇺|🇬🇷|🇵🇹|🇦🇹|🇱🇹|🇱🇻|🇷🇴|🇨🇿|🌍|🇺🇦|🇬🇧|🇷🇺|🇮🇪|🇸🇰|🇧🇬|🇷🇸|🇭🇷|🇲🇨)


#策略分组
proxy-groups:
  - name: Proxy
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:  
    use: 
      - Nexitally_Filter_All       
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: Manual proxy
    type: select
    proxies:  
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All
 

  - name: Game
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All
       
  - name: YouTube
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: TelegramSG
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: TelegramUS
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: TelegramEU
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: GoogleVoice
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: Google
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: Netflix
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: Disney
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: HBO
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: BiliBili
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: Spotify
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: OpenAI
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  

  - name: Emby
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: Instagram
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: TikTok
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: Twitter
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All


  - name: Microsoft
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: Amazon
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All

  - name: Download
    type: select
    proxies:
      - Proxy
      - 香港节点(url-test)
      - 台湾节点(url-test)
      - 新加坡节点(url-test)
      - 日本节点(url-test)
      - 美国节点(url-test)
      - 欧洲节点(url-test)
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)     
      - Kuromi日本节点(url-test)     
      - Kuromi美国节点(url-test)  
      - Kuromi欧洲节点(url-test)  
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - 香港节点散列
      - 台湾节点散列
      - 新加坡节点散列   
      - 日本节点散列
      - 美国节点散列
      - 欧洲节点散列
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - 香港节点轮询
      - 台湾节点轮询
      - 新加坡节点轮询   
      - 日本节点轮询
      - 美国节点轮询
      - 欧洲节点轮询
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - 香港节点(select)
      - 台湾节点(select)
      - 新加坡节点(select)
      - 日本节点(select)
      - 美国节点(select)
      - 欧洲节点(select)
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)  
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport欧洲节点(select)  
      - Nexitally
      - Kuromi
      - Chinaairport   
      - DIRECT
    use:        
      - Nexitally_Filter_All
      - Kuromi_Filter_All
      - Chinaairport_Filter_All
      
  - name: Nexitally
    type: select
    proxies:
      - Nexitally香港节点(url-test)
      - Nexitally台湾节点(url-test)
      - Nexitally新加坡节点(url-test)
      - Nexitally日本节点(url-test)
      - Nexitally美国节点(url-test)
      - Nexitally欧洲节点(url-test)
      - Nexitally香港节点散列
      - Nexitally台湾节点散列
      - Nexitally新加坡节点散列
      - Nexitally日本节点散列
      - Nexitally美国节点散列
      - Nexitally欧洲节点散列
      - Nexitally香港节点轮询
      - Nexitally台湾节点轮询
      - Nexitally新加坡节点轮询
      - Nexitally日本节点轮询
      - Nexitally美国节点轮询
      - Nexitally欧洲节点轮询
      - Nexitally香港节点(select)
      - Nexitally台湾节点(select)
      - Nexitally新加坡节点(select)
      - Nexitally日本节点(select)     
      - Nexitally美国节点(select)
      - Nexitally欧洲节点(select)
    use:        
      - Nexitally_Filter_All
    
  - name: Kuromi
    type: select
    proxies:
      - Kuromi香港节点(url-test)
      - Kuromi台湾节点(url-test)
      - Kuromi新加坡节点(url-test)
      - Kuromi日本节点(url-test)
      - Kuromi美国节点(url-test)
      - Kuromi欧洲节点(url-test)
      - Kuromi香港节点散列
      - Kuromi台湾节点散列
      - Kuromi新加坡节点散列
      - Kuromi日本节点散列
      - Kuromi美国节点散列
      - Kuromi欧洲节点散列
      - Kuromi香港节点轮询
      - Kuromi台湾节点轮询
      - Kuromi新加坡节点轮询
      - Kuromi日本节点轮询
      - Kuromi美国节点轮询
      - Kuromi欧洲节点轮询
      - Kuromi香港节点(select)
      - Kuromi台湾节点(select)
      - Kuromi新加坡节点(select)
      - Kuromi日本节点(select)
      - Kuromi美国节点(select)
      - Kuromi欧洲节点(select)
    use:        
      - Kuromi_Filter_All

  - name: Chinaairport
    type: select
    icon: https://raw.githubusercontent.com/airportchat/Logo/main/airport_logo/Tag.png
    proxies:
      - Chinaairport香港节点(url-test)
      - Chinaairport台湾节点(url-test)
      - Chinaairport新加坡节点(url-test)
      - Chinaairport日本节点(url-test)
      - Chinaairport美国节点(url-test)
      - Chinaairport欧洲节点(url-test)
      - Chinaairport香港节点散列
      - Chinaairport台湾节点散列
      - Chinaairport新加坡节点散列
      - Chinaairport日本节点散列
      - Chinaairport美国节点散列
      - Chinaairport欧洲节点散列
      - Chinaairport香港节点轮询
      - Chinaairport台湾节点轮询
      - Chinaairport新加坡节点轮询
      - Chinaairport日本节点轮询
      - Chinaairport美国节点轮询
      - Chinaairport欧洲节点轮询
      - Chinaairport香港节点(select)
      - Chinaairport台湾节点(select)
      - Chinaairport新加坡节点(select)
      - Chinaairport日本节点(select)
      - Chinaairport美国节点(select)
      - Chinaairport欧洲节点(select)
    use:        
      - Chinaairport_Filter_All

  - name: Advertising
    type: select
    proxies:
      - REJECT
      - DIRECT
  - name: AdvertisingTest
    type: select
    proxies:
      - REJECT
      - DIRECT
  - name: AdGuardSDNSFilter
    type: select
    proxies:
      - REJECT
      - DIRECT
  - name: AdvertisingLite
    type: select
    proxies:
      - REJECT
      - DIRECT

#Nexitally部分
  - name: Nexitally香港节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_HK
      
  - name: Nexitally台湾节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_TW

  - name: Nexitally新加坡节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_SG

  - name: Nexitally美国节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_US

  - name: Nexitally日本节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_JP

  - name: Nexitally欧洲节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_EU
      
  - name: Nexitally香港节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_HK

  - name: Nexitally台湾节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_TW

  - name: Nexitally日本节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_JP

  - name: Nexitally新加坡节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_SG

  - name: Nexitally美国节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_US

  - name: Nexitally欧洲节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_EU

  - name: Nexitally香港节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_HK

  - name: Nexitally台湾节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_TW

  - name: Nexitally新加坡节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_SG

  - name: Nexitally日本节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_JP

  - name: Nexitally美国节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_US

  - name: Nexitally欧洲节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_EU
      
  - name: Nexitally香港节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_HK

  - name: Nexitally台湾节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_TW

  - name: Nexitally新加坡节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_SG

  - name: Nexitally日本节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_JP

  - name: Nexitally美国节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_US

  - name: Nexitally欧洲节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_EU


#Kuromi部分
  - name: Kuromi香港节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_HK

  - name: Kuromi台湾节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_TW

  - name: Kuromi新加坡节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_SG

  - name: Kuromi美国节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_US

  - name: Kuromi日本节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_JP

  - name: Kuromi欧洲节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_EU
      
  - name: Kuromi香港节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_HK

  - name: Kuromi台湾节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_TW

  - name: Kuromi日本节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_JP


  - name: Kuromi新加坡节点(url-test)
    type: url-test
    url: "http://cp.cloudflare.com/generate_204" 
    interval: 120
    proxies:
    use:
      - Kuromi_Filter_SG

  - name: Kuromi美国节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_US

  - name: Kuromi欧洲节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_EU

  - name: Kuromi香港节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_HK

  - name: Kuromi台湾节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_TW

  - name: Kuromi新加坡节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_SG

  - name: Kuromi日本节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_JP

  - name: Kuromi美国节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_US

  - name: Kuromi欧洲节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_EU
      
  - name: Kuromi香港节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_HK

  - name: Kuromi台湾节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_TW

  - name: Kuromi新加坡节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_SG

  - name: Kuromi日本节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_JP

  - name: Kuromi美国节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_US

  - name: Kuromi欧洲节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Kuromi_Filter_EU



#Chinaairport部分
  - name: Chinaairport香港节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_HK

  - name: Chinaairport台湾节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_TW

  - name: Chinaairport新加坡节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_SG

  - name: Chinaairport美国节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_US

  - name: Chinaairport日本节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_JP

  - name: Chinaairport欧洲节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_EU

  - name: Chinaairport香港节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_HK

  - name: Chinaairport台湾节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_TW

  - name: Chinaairport日本节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_JP

  - name: Chinaairport新加坡节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_SG

  - name: Chinaairport美国节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_US

  - name: Chinaairport欧洲节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_EU

  - name: Chinaairport香港节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_HK

  - name: Chinaairport台湾节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_TW

  - name: Chinaairport新加坡节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_SG

  - name: Chinaairport日本节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_JP

  - name: Chinaairport美国节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_US

  - name: Chinaairport欧洲节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_EU
 
  - name: Chinaairport香港节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_HK

  - name: Chinaairport台湾节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_TW

  - name: Chinaairport新加坡节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_SG

  - name: Chinaairport日本节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_JP

  - name: Chinaairport美国节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_US

  - name: Chinaairport欧洲节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Chinaairport_Filter_EU

      
  - name: 香港节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_HK
      - Kuromi_Filter_HK
      - Chinaairport_Filter_HK

  - name: 台湾节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_TW
      - Kuromi_Filter_TW
      - Chinaairport_Filter_TW

  - name: 日本节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_JP
      - Kuromi_Filter_JP
      - Chinaairport_Filter_JP

  - name: 新加坡节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_SG
      - Kuromi_Filter_SG
      - Chinaairport_Filter_SG

  - name: 美国节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_US
      - Kuromi_Filter_US
      - Chinaairport_Filter_US

  - name: 欧洲节点(select)
    type: select
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_EU
      - Kuromi_Filter_EU
      - Chinaairport_Filter_EU

  - name: 香港节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_HK
      - Kuromi_Filter_HK
      - Chinaairport_Filter_HK

  - name: 台湾节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_TW
      - Kuromi_Filter_TW
      - Chinaairport_Filter_TW

  - name: 日本节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_JP
      - Kuromi_Filter_JP
      - Chinaairport_Filter_JP

  - name: 新加坡节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_SG
      - Kuromi_Filter_SG
      - Chinaairport_Filter_SG

  - name: 美国节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_US
      - Kuromi_Filter_US
      - Chinaairport_Filter_US

  - name: 欧洲节点(url-test)
    type: url-test
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_EU
      - Kuromi_Filter_EU
      - Chinaairport_Filter_EU

  - name: 香港节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204 
    proxies:
    use:
      - Nexitally_Filter_HK
      - Kuromi_Filter_HK
      - Chinaairport_Filter_HK

  - name: 台湾节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_TW
      - Kuromi_Filter_TW
      - Chinaairport_Filter_TW

  - name: 日本节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_JP
      - Kuromi_Filter_JP
      - Chinaairport_Filter_JP

  - name: 新加坡节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_SG
      - Kuromi_Filter_SG
      - Chinaairport_Filter_SG

  - name: 美国节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_US
      - Kuromi_Filter_US
      - Chinaairport_Filter_US

  - name: 欧洲节点散列
    type: load-balance
    strategy: consistent-hashing
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_EU
      - Kuromi_Filter_EU
      - Chinaairport_Filter_EU
      
  - name: 香港节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204 
    proxies:
    use:
      - Nexitally_Filter_HK
      - Kuromi_Filter_HK
      - Chinaairport_Filter_HK

  - name: 台湾节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_TW
      - Kuromi_Filter_TW
      - Chinaairport_Filter_TW

  - name: 日本节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_JP
      - Kuromi_Filter_JP
      - Chinaairport_Filter_JP

  - name: 新加坡节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_SG
      - Kuromi_Filter_SG
      - Chinaairport_Filter_SG

  - name: 美国节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_US
      - Kuromi_Filter_US
      - Chinaairport_Filter_US

  - name: 欧洲节点轮询
    type: load-balance
    strategy: round-robin
    health-check:
      url: "http://cp.cloudflare.com/generate_204"
      interval: 120
      timeout: 5000
      expected-status: 204
    proxies:
    use:
      - Nexitally_Filter_EU
      - Kuromi_Filter_EU
      - Chinaairport_Filter_EU



#远程规则集合
rule-providers:
  #Game
  Game_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/ccc52266/CC/main/README.md"
    path: ./RuleSet/Game.yaml
    interval: 10400

  #Telegram
  TelegramSG_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/ccc52266/embyh/main/README.md"
    path: ./RuleSet/TelegramSG.yaml
    interval: 10400

  TelegramUS_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/ccc52266/TelegramUS/main/README.md"
    path: ./RuleSet/TelegramUS.yaml
    interval: 10400
    
  TelegramEU_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/ccc52266/TelegramEU/main/README.md"
    path: ./RuleSet/TelegramEU.yaml
    interval: 10400

  #放行
  Direct_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Direct/Direct.yaml"
    path: ./RuleSet/Direct.yaml
    interval: 10400
  #去广告
  Advertising_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Advertising/Advertising_Classical.yaml"
    path: ./RuleSet/Advertising.yaml
    interval: 10400

  AdvertisingTest_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/AdvertisingTest/AdvertisingTest_Classical.yaml"
    path: ./RuleSet/AdvertisingTest.yaml
    interval: 10400
        
  AdGuardSDNSFilter_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/AdGuardSDNSFilter/AdGuardSDNSFilter_Classical.yaml"
    path: ./RuleSet/AdGuardSDNSFilter_Classical.yaml
    interval: 10400
    
  AdvertisingLite_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/AdvertisingLite/AdvertisingLite_Classical.yaml"
    path: ./RuleSet/AdvertisingLite.yaml
    interval: 10400
    

  #常用下载软件
  Download_rule:
    type: http
    behavior: classical
    url: "https://ghproxy.com/https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Download/Download.yaml"
    path: ./RuleSet/Download.yaml
    interval: 10400

  Emby_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/ccc52266/Emby/main/README.md"
    path: ./RuleSet/Emby.yaml
    interval: 10400
  
  #流媒体
  YouTube_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/YouTube/YouTube.yaml"
    path: ./RuleSet/YouTube.yaml
    interval: 10400

  Netflix_rule:
    type: http
    behavior: classical
    url: "https://ghproxy.com/https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Netflix/Netflix.yaml"
    path: ./RuleSet/Netflix.yaml
    interval: 10400

  HBO_rule:
    type: http
    behavior: classical
    url: "https://ghproxy.com/https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/HBO/HBO.yaml"
    path: ./RuleSet/HBO.yaml
    interval: 10400

  Disney_rule:
    type: http
    behavior: classical
    url: "https://ghproxy.com/https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Disney/Disney.yaml"
    path: ./RuleSet/Disney.yaml
    interval: 10400

  #Microsoft
  Microsoft_rule:
    type: http
    behavior: classical
    url: "https://ghproxy.com/https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Microsoft/Microsoft.yaml"
    path: ./RuleSet/Microsoft.yaml
    interval: 10400

  #OpenAI
  OpenAI_rule:
    type: http
    behavior: classical
    url: "https://ghproxy.com/https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/OpenAI/OpenAI.yaml"
    path: ./RuleSet/OpenAI.yaml
    interval: 10400

  #Spotify
  Spotify_rule:
    type: http
    behavior: classical
    url: "https://ghproxy.com/https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Spotify/Spotify.yaml"
    path: ./RuleSet/Spotify.yaml
    interval: 10400

  #TikTok
  TikTok_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/TikTok/TikTok.yaml"
    path: ./RuleSet/TikTok.yaml
    interval: 10400

  #Google
  GoogleCN_rule:
    type: http
    behavior: classical
    url: "https://github.com/ACL4SSR/ACL4SSR/blob/master/Clash/Ruleset/GoogleCN.list"
    path: ./RuleSet/GoogleCN.list
    interval: 10400
    
  GoogleCNProxyIP_rule:
    type: http
    behavior: classical
    url: "https://github.com/ACL4SSR/ACL4SSR/blob/master/Clash/Ruleset/GoogleCNProxyIP.list"
    path: ./RuleSet/GoogleCN.list
    interval: 10400
    
  Google_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Google/Google.yaml"
    path: ./RuleSet/Google.yaml
    interval: 10400
    
  GoogleFCM_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/GoogleFCM/GoogleFCM.yaml"
    path: ./RuleSet/GoogleFCM.yaml
    interval: 10400
    
  #Twitter
  Twitter_rule:
    type: http
    behavior: classical
    url: "https://ghproxy.com/https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Twitter/Twitter.yaml"
    path: ./RuleSet/Twitter.yaml
    interval: 10400
    
  DouYin_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/ccc52266/douyin/main/README.md"
    path: ./RuleSet/DouYin.yaml
    interval: 10400

  #Instagram
  Instagram_rule:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Instagram/Instagram.yaml"
    path: ./RuleSet/Instagram.yaml
    interval: 10400


#本地规则
rules:
  #Game
  - RULE-SET,Game_rule,Game
  
  #Telegram
  - RULE-SET,TelegramSG_rule,TelegramSG
  - RULE-SET,TelegramUS_rule,TelegramUS
  - RULE-SET,TelegramEU_rule,TelegramEU

  # OpenAI
  - RULE-SET,OpenAI_rule,OpenAI
  
  # Microsoft
  - RULE-SET,Microsoft_rule,Microsoft
 
  # 媒体
  - RULE-SET,YouTube_rule,YouTube
  - RULE-SET,Netflix_rule,Netflix
  - RULE-SET,Disney_rule,Disney
  - RULE-SET,HBO_rule,HBO

  # Google
  - RULE-SET,GoogleCN_rule,DIRECT
  - RULE-SET,GoogleCNProxyIP_rule,DIRECT
  - PROCESS-NAME,com.google.android.apps.googlevoice,GoogleVoice
  - DOMAIN,lens.l.google.com,GoogleVoice
  - DOMAIN,voice.googleapis.com,GoogleVoice
  - RULE-SET,Google_rule,Google
  - RULE-SET,GoogleFCM_rule,DIRECT
  # 音乐
  - RULE-SET,Spotify_rule,Spotify

  # 社交APP
  - RULE-SET,Instagram_rule,Instagram
  - RULE-SET,TikTok_rule,TikTok
  - RULE-SET,Twitter_rule,Twitter
 
  #常用下载软件
  - RULE-SET,Download_rule,Download
  - RULE-SET,Emby_rule,Emby
  - RULE-SET,DouYin_rule,TikTok
  - DOMAIN-SUFFIX,biliapi.com,BiliBili
  - DOMAIN-SUFFIX,biliapi.net,BiliBili
  - DOMAIN-SUFFIX,bilibili.com,BiliBili
  - PROCESS-NAME,tv.danmaku.bili,BiliBili
  
  #放行
  - RULE-SET,Direct_rule,DIRECT
  # AdGuardSDNSFilter
  - RULE-SET,AdGuardSDNSFilter_rule,AdGuardSDNSFilter
  - RULE-SET,Advertising_rule,Advertising
  - RULE-SET,AdvertisingTest_rule,AdvertisingTest
  - RULE-SET,AdvertisingLite_rule,AdvertisingLite
  
  #中国
  - GeoIP,CN,DIRECT
  # 必须
  - MATCH,Manual proxy
