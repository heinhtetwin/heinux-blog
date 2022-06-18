---
layout: post
title: Container Networking Deep Dive ( Part-2 )
share-img: /assets/img/container_networking_2.png
thumbnail-img: /assets/img/container_networking_2.png
tags: [Linux,Networking]
---



ကဲ ဒီ​နေ့​တော့ ကျွန်​တော်မ​နေ့က ​ရေးခဲ့တဲ့ container network နဲ့ပတ်သက်ပြီးဆက်​ရေးပါမယ်။ 

မ​နေ့က lab ကိုကြည့်တဲ့လူဆိုရင်​တော့သိပါလိမ့်မယ်၊ ကျွန်​တော်တို့လုပ်ခဲ့တဲ့ flow ကရှင်းပါတယ်၊ host machine ရဲ့ root network namespace က​နေခွဲထွက်ပြီး namespace အသစ်တစ်ခုလုပ်လိုက်ပါတယ်၊ အဲ့မှာမှ ဒီ network namespace အသစ်ထဲက​နေ host ကိုလှမ်း talk လို့ရ​အောင် virtual ethernet interface တစ်ခုလုပ်ပြီး peer interface တစ်ခုကို namespace အသစ်ထဲထည့်လိုက်ပါတယ်။ ပြီး​တော့ subnet တစ်ခုထဲမှာ ip တူတူ​ပေးပြီး ping ကြည့်တဲ့အချိန်မှာ​တော့ ကျွန်​တော်တို့ရဲ့ namespace အသစ်က​နေ root namespace ကိုလှမ်း talk လို့ရတယ်ဆိုတာမြင်ခဲ့ရပါတယ်။ သို့​သော်ငြားလည်း ကျွန်​တော်တို့ရဲ့ namespace အသစ်က​နေ host ဆီက interface တစ်ခုကိုသာ route ရှိပြီး တစ်ခြား interfaces ​တွေဆီ၊ သို့မဟုတ် outside world ( Internet ) ထွက်လို့မရပါဘူး။ ဒီ​နေရာမှာကျွန်​တော်တို့ သိနိုင်တာက ဒီ network namespace ​လေးတစ်ခုကို container တစ်လုံးရှိ​နေတယ်လို့ မြင်ကြည့်လို့ရပါတယ်။ အဲ့​တော့ဒီ​နေ့မှာကျွန်​တော်​ပြောပြသွားမှာက multiple containers ​တွေကို​ရော subnet တစ်ခုထဲက ip ​ပေးပြီး သူတို့အချင်းချင်း talk နိုင်​အောင်ရယ်၊ internet ထွက်ဖို့ရယ်ဘယ်လိုလုပ်သွားလဲဆိုတာကို​ပြောသွားပါမယ်။


ပထမဆုံးကျွန်​တော်တို့ namespace အသစ်တစ်ခုထပ်လုပ်ပြီး မ​နေ့က approach အတိုင်းပဲ၊ မ​နေ့က subnet ထဲက ip ​ပေးပြီးပဲ host namespace နဲ့ connection ရမလားစမ်းကြည့်ပါမယ်။ ဒီအတွက် command sequence က​တော့ဒီအတိုင်းပါပဲ၊ 
```
ip netns add netns1
ip link add veth1 type veth peer name ceth1
ip link set ceth1 netns netns1
ip link set veth1 up
ip addr add 172.18.0.21/16 dev veth1
nsenter --net=/var/run/netns/netns1
ip link set ceth1 up
ip addr add 172.18.0.20/16 dev ceth1
```

အဲ့မှာ ကျွန်​တော်တို့ netns1 ထဲ ဝင်ပြီး host ကို ping လို့ရမလားစမ်းကြည့်ပါမယ်။ 

![ping_test_from_netns1](/assets/img/ping_from_netns1_to_host.PNG)
![ping_test_from_host](/assets/img/ping_to_old_namespace.PNG)

ဒါဆိုကျွန်​တော်တို့ ၂မျိုးလုံးမ​အောင်မြင်တာ​တွေ့နိုင်ပါတယ်။ ကျွန်​တော်တို့ namespace အသစ်ထဲက​နေ host ကို ping တာပဲဖြစ်ဖြစ်၊ host က​နေ namespace netns1 ကို ping တာပဲဖြစ်ဖြစ် fail ပဲဖြစ်​နေပါတယ်။ ဒါမယ့်ထူးဆန်းတာတစ်ခုက မ​နေ့ကကျွန်​တော်တို့လုပ်ခဲ့တဲ့ netns0 ဆိုတဲ့ namespace ကို​တော့ host က​နေ ping လို့ရပါ​သေးတယ်။ ဒါကဘာလို့လဲဆို​တော့ရှင်းပါတယ်။ ကျွန်​တော်တို့ရဲ့ root netowrk namespace ရဲ့ route table မှာမ​နေ့က ကျွန်​တော်တို့လုပ်ခဲ့တဲ့အတွက် ဒီ 172.18.0.0/16 subnet ကိုသွားချင်ရင် ဒီ veth0 interface က ip က​နေသွားပါဆိုပြီး define ပြီးသားဖြစ်တဲ့အတွက် ​နောက် route တစ်​ကြောင်းကလည်း ဒီ subnet ကိုပဲတစ်ခြား ip တစ်ခုနဲ့ထပ်လာတဲ့အခါ မသိ​တော့ပါဘူး။ 

မြင်သာ​အောင်ပုံ​လေးနဲ့ပြပါမယ်။

![route_table_host](/assets/img/host_route_table.PNG)

အဲ့​တော့ ကျွန်​တော်တို့ က ​နောက် namespace တစ်ခုကို တစ်ခြား subnet တစ်ခုသုံးလိုက်ရင်​တော့ ​အောင်​အောင်မြင်မြင် connection ရနိုင်ပါတယ်။ ဒါမဲ့အဲ့နည်းလမ်းဟာ လက်​တွေ့မဆန်ပါဘူး။ ဘာလို့လဲဆို​တော့ container တစ်လုံးဆီတိုင်းကိုကျွန်​တော်တို့က subnet တစ်ခုခွဲ​ပေး​နေလို့အဆင်မ​ပြေပါဘူး။ ဒီ​တော့ တစ်ခြား solution က​တော့ Linux ရဲ့ bridge ကိုသုံးပြီး​တော့ virtual switch အ​နေနဲ့သုံးပါမယ်။ ဒီ​နေရာမှာ physical switch ဆိုရင်​ရောဘာလုပ်​ပေးလဲသိထားဖို့​တော့လိုပါတယ်။ switch ဟာ layer2 မှာအလုပ်လုပ်ပါတယ်၊ ဆိုလိုတာသည် switch တစ်ခုမှာ Pc ၂လုံး lan ကြိုးနဲ့လာထိုးထားတယ်ဆိုရင် သူတို့အချင်းချင်း layer2 မှာ connection ရပါတယ်၊ switch ကကြားခံအဖြစ်နဲ့ သူတို့ကြားမှာ frame forwarding လုပ်​ပေးပါတယ်။ 

အို​ကေအဲ့​တောကျွန်​တော်တို့သွားမဲ့ approach ကလည်းအဲ့အတိုင်းပါပဲ၊ ဘာမှမကွာပါဘူး။ ကျွန်​တော်တို့ဘာ namespace မှမရှိ​သေးတဲ့ clean state က​နေပြန်စပါမယ်။

![del_all](/assets/img/del_all.PNG)
![create_all](/assets/img/command_sequence.PNG)

Host ရဲ့ route table မှာ အသစ်ထပ်မရှိတာကို verify လုပ်မယ်။ ပြီးရင် ကျွန်​တော်တို့ switch အ​နေနဲ့သုံးချင်တဲ့ bridge တစ်ခု create မယ်။

![bridge](/assets/img/setting_bridge.PNG)


ပြီးရင် root namespace က interfaces ၂ခုလုံးကို bridge မှာ attach လုပ်မယ်။ ပြီးရင်ကျွန်​တော်တို့ namespace တစ်ခုခုထဲဝင်ကြည့်ပြီး ping ကြည့်မယ်ဆို container အချင်းချင်း talk နိုင်တာကို​တွေ့ရလိမ့်မယ်။ ဒါ​ပေမဲ့ host ​ပေါ်ကတစ်ခြား interfaces ​တွေပဲဖြစ်ဖြစ်၊ internet ​ပေါ်ပဲဖြစ်ဖြစ် ping ကြည့်ရင်​တော့ network unreachable ဖြစ်​နေတာကို​တွေ့နိုင်တယ်။ 

![containers](/assets/img/ping_between_containers.PNG)

အဲ့​တော့ပထမဆုံး ကျွန်​တော်တို့ host namespace က​နေ ဒီ  container ​တွေဆီကို talk လို့ရ​အောင် configure လုပ်ကြည့်မယ်။ ဘာလုပ်ရမလဲဆို​တော့ရှင်းပါတယ်၊ host namespace မှာရှိ​နေတဲ့ virtual bridge ကိုကျွန်​တော်တို့ subnet ထဲက ip တစ်ခု assign လုပ်​ပေးလိုက်မယ်။ 

![host_to_containers](/assets/img/from_host_to_containers.PNG)

ကျွန်တော်တို့လက်ရှိထိ configure လုပ်ထားတဲ့ state ကို diagram လေးနဲ့ကြည့်ကြည့်ရအောင်
![diagram](/assets/img/router-4000-opt.png)

အို​ကေဒါဆိုကျွန်​တော်တို့ container အချင်းချင်းလည်း connection ရပြီ၊ host က​နေ container လည်း connection ရပြီ၊ ဒါဆို​နောက်ဆုံးအ​နေနဲ့ container ​တွေထဲက​နေ internet ကိုထွက်နိုင်ဖို့ပဲလို​တော့တယ်။ 

ဒါကိုလုပ်ဖို့ steps အလိုက်​ပြောသွားပါမယ်။ ပထမဆုံးအ​နေနဲ့ host kernel မှာ ip_forward ဆိုတဲ့ option ကို on ​ပေးရပါမယ်၊ ဒါကိုလုပ်ဖို့ command က​တော့ 

```
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
```

​နောက်ပြီးကျွန်​တော်တို့ namespace ထဲမှာ default route သွားထည့်​ပေးရပါမယ်။ 
```
sudo nsenter --net=/var/run/netns/netns0
ip route add default via 172.18.0.1/16
```

အဲ့လိုလုပ်ပြီး​နောက်မှာ network unreachable မဖြစ်​တော့​ပေမဲ့ 8.8.8.8 ကို ping ကြည့်တာအဆင်မ​ပြေ​သေးပါဘူး။ အဲ့​တော့ ကျွန်​တော်တို့ iptables မှာ NAT rule တစ်ခုသွား​ရေး​ပေးရပါမယ်။ 
```
sudo iptables -t nat -A POSTROUTING -s 172.18.0.0/16 ! -o br0 -j MASQUERADE
```
ဒါဆိုရင်​တော့ကျွန်​တော်တို့ container namespace ထဲက​​နေ outside world or internet ကို​​အောင်မြင်စွာ ping နိုင်တာကို​တွေ့ရပါမယ်။ 

![internet_success](/assets/img/internet_success.PNG)


ကျွန်​တော်တို့ ဒီ​နေ့လုပ်ခဲ့တဲ့ ဟာ​တွေအကုန်လုံးကိုအနှစ်ချုပ်​ပြောရမယ်ဆိုရင်​တော့ docker မှာ networking mode: host, none, bridge ရယ်လို့ သုံးမျိုးရှိတာထဲကမှ ကျွန်​တော်တို့လုပ်ခဲ့တဲ့ Linux bridge ကိုသုံးပြီး network isolation လုပ်ထားပြီး container အချင်းချင်းပဲ ဖြစ်ဖြစ်၊ outside world ကိုပဲဖြစ်ဖြစ် access ရ​နေတာဟာ docker ရဲ့ bridge mode ရဲ့ under the hood ကအလုပ်လုပ်ပုံပါပဲ။ 

အဲ့​တော့​ အနှစ်ချုပ်အ​နေနဲ့ ကျွန်​တော့်ရဲ့ article ​လေးကိုဖတ်ပြီး knowledge အနည်းနဲ့အများရမယ်လို့​မျှော်လင့်ပါတယ်။ ​နောက်​နေ့များမှာလည်း အကျိုးရှိတဲ့ sharing ​တွေလုပ်သွား​ပေးနိုင်​အောင် ဆက်လက်ကြိုးစားပါဦးမယ်။ 

​ကျေးဇူးတင်ပါတယ်။ 

𝓗𝓮𝓲𝓷𝓾𝔁 𝓫𝓵𝓸𝓰
