---
layout: post
title: Container Networking Deep Dive ( Part-1 )
share-img: /assets/img/Is Container Networking Simple.png
thumbnail-img: /assets/img/Is Container Networking Simple.png
tags: [Linux,Networking]
---

အို​ကေ ဒီ​နေ့မှာ​တော့ ကျွန်​တော်က container networking လွယ်သလား ခက်သလား ဆိုတဲ့​ခေါင်းစဥ်​လေးနဲ့ sharing လုပ်သွားချင်ပါတယ်။ 

ဒီ​ခေါင်းစဥ်နဲ့ ​ပြောရတဲ့အ​ကြောင်းက​တော့ အများစုက container docker ဆိုပြီးအကြမ်းဖျင်း ပါးစပ်ထဲ​ပြော​နေကြ​ပေမဲ့ under the hood မှာ networking ဘက်ကကြည့်ရင် ဘယ်လိုအလုပ်လုပ်လဲဆိုတာကို beginners ​တွေကိုရှင်းမပြကြပါဘူး။ ကျွန်​တော်ကိုယ်တိုင်လည်း ​လေ့လာ​နေဆဲဖြစ်တာမို့ ဒါနဲ့ပတ်သက်ပြီး ဒီ​နေ့မှာ​တော့ နားလည်သ​လောက်ပြန်​ပြောသွားပါမယ်။ 

အို​ကေအဲ့​တော့ ​ခေါင်းစဥ်နဲ့လိုက်​​အောင်ပထမဆုံး container ထဲက networking ရိုးရှင်းလားဆိုတာကို စ​ဖြေပါမယ်။ မရိုးရှင်းပါဘူး။ ဒါ​ပေမဲ့ အရမ်းခက်​​နေသလားဆိုရင်လည်း မခက်ပါဘူး။ အို​ကေ ​လေရှည်တာများ​နေပြီ၊ လိုရင်းကိုသွားလိုက်ကြရ​အောင်... 

Container တစ်လုံးဆိုတာကို lightweight vm တစ်လုံးလို့အရင်စဥ်းစားကြည့်ရ​အောင်၊ အဲ့​တော့ ဒီ container ​လေးဟာ physical host ​ပေါ်မှာရှိရင်ရှိမယ်၊ ဒါမှမဟုတ် virtualized လုပ်ထားတဲ့ vm ထဲမှာရှိချင်လည်းရှိမယ်​ပေါ့၊ ဒီ​တော့ container က vm နဲ့ဘာကွာသွားလဲဆိုရင် vm ​တွေဟာ hypervisor တစ်ခုခု၊ ဒါမှမဟုတ် OS တင်ထားပြီးတဲ့ computer တစ်ခုခုထဲမှာ ကျွန်​တော်တို့က guest OS ​​နောက်တစ်ခုထပ်တင်ပြီး သုံးတာဖြစ်တဲ့အတွက် physical computer တစ်လုံးလိုပဲ vm တစ်လုံးက components အပြည့်အဝ ပါပါတယ်။ ဆိုလိုတာသည် သူ့ kernel နဲ့သူရှိပြီး ​အောက်က သူ့ကိုသတ်မှတ်​ပေးထားတဲ့ underlying hardware resources ​တွေကိုကိုယ်တိုင် manage လုပ်ပါတယ်။ Container တိုင်းမှာ​တော့ အဲ့လိုမဟုတ်ပဲ Guest OS တင်စရာမလိုပါဘူး၊ ကျွန်​တော်တို့ရဲ့ Host OS မှာပဲရှိ​နေတာဖြစ်ပြီး အလွယ်​ပြောရရင် Linux OS ထဲမှာရှိတဲ့ isolated လုပ်ထားတဲ့ process တစ်ခုလိုစဥ်းစားကြည့်ရ​အောင်..ဆို​တော့ containers ​တွေရယ်လို့ဖြစ်လာ​အောင် အဓိက ကူညီပံ့ပိုး​ပေးတာက​တော့ Linux kernel features ​တွေဖြစ်တဲ့ namespaces and cgroups လို့​ခေါ်တဲ့ features ​တွေပဲဖြစ်ပါတယ်။


ဒီပို့စ်မှာ​တော့ကျွန်​တော်က network namespace နဲ့ပတ်သက်ပြီး အဓိက​ပြောသွားမှာပါ။ Namespaces လို့​ပြောရင် network namespace တစ်ခုထဲရှိတာ​တော့မဟုတ်ပါဘူး၊ တစ်ခြား user namespace, process namespace ​တွေလည်းရှိပါ​သေးတယ်။ အို​ကေ အဲ့​တော့ network namespace ဆိုတာဘာလဲ ? 

အ​ဖြေက​တော့ရှင်းပါတယ်။ namespace ဆိုတာကို ကျွန်​တော်တို့ ​​ထောင်တစ်ခုထဲမှာ အခန်း​တွေခွဲထားတာနဲ့ ယှဥ်ပြီးစဥ်းစားကြည့်ရ​အောင်၊ ​ထောင်သားတစ်​ယောက်ဆီဟာ သူတို့ကိုယ်ပိုင်အခန်းတစ်ခုဆီ ရှိပါတယ်။ သူတို့အခန်းကို​တော့သူတို့အပိုင်ပါပဲ၊ ဒါ​ပေမဲ့ သူတို့ အပြင်ကို access လုပ်လို့မရပါဘူး။ ​ပြောချင်တာသည် namespace တစ်ခုတိုင်းဆီမှာရှိတဲ့ container ​တွေသည်သူတို့ကိုယ်ပိုင် သီးသန့် network stack ရှိပါတယ်။ အဲ့ stack ထဲမှာဘာ​တွေပါလဲဆိုရင် network routes ​တွေ, virtual interface (veth) ​တွေ, ပြီးရင် firewall rules ​တွေ တစ်ခုချင်းဆီအတွက် သီးသန့်ရှိပါတယ်။ ဆို​တော့ ဒီ isolated လုပ်ထားတဲ့ environment ထဲက​နေ host ကို talk ချင်တာဖြစ်ဖြစ် outside world ကို internet access ရချင်တာပဲ ဖြစ်ဖြစ်ဆိုရင် သူတို့ကိုယ်ပိုင် routes ရှိဖို့လိုပါတယ်။ အဲ့တာကိုရဖို့ ဒီ​နေ့မှာ​တော့ Virtual Ethernet devices ကိုသုံးပြီးဘယ်လိုလုပ်ရမဲ ​ပြောပြသွားပါမယ်။ 

ပထမဆုံးကျွန်တော်တို့ရဲ့ Root Network Namespace မှာဘာတွေရှိလဲအရင်ကြည့်ကြည့်မယ်။ အဲ့တာကိုကြည့်ဖို့ script တစ်ခုရေးထားတယ်၊ အဲ့ script မှာဘာတွေပါလဲအရင်ကြည့်ကြည့်ရအောင်

![net-check-sh](/assets/img/checknet.PNG)

အဲ့ script လေးကို run ကြည့်ပါမယ်

![host-netstack](/assets/img/Host_net_check.PNG)

နောက်တစ်ဆင့်အနေနဲ့ ကျွန်​တော်တို့ host ရဲ့ network stack မဟုတ်ပဲ network stack အသစ်တစ်ခုလုပ်ကြည့်မယ်။ 
```
sudo ip netns add netns0 
```
အဲ့တာကိုအသုံးပြုဖို့ nsenter command ကိုသုံးမယ်။ 
```
sudo nsenter --net=/var/run/netns/netns0 bash 
```
ဆိုရင်ကျွန်​တော်တို့က ပုံမှန် host ရဲ့ network stack ထဲမဟုတ်ပဲ ကျွန်​တော်တို့အသစ်လုပ်ထားတဲ့ network stack ထဲ​ရောက်သွားမယ်။ 

![netns0-netstack](/assets/img/netns0__net_check.PNG) 

ဒါဆိုရင်အဲ့ netns0 namespace ထဲမှာရှိတဲ့ network stack တွေကမတူညီတာကိုတွေ့ရပါမယ်။


Container network ထဲက​နေ Host ကိုလှမ်း talk လို့ရ​အောင် virtual ethernet device တစ်ခုလုပ်မယ်။ 
```
sudo ip link add veth0 type veth peer name ceth0 
```
![new-veth](/assets/img/add_new_veth.PNG)
ဒီ  command ​လေးလုပ်​ပေးသွားတာက အချင်းချင်း connect ဖြစ်​နေတဲ့ ကြိုးတစ်​ချောင်းက အစ ၂စလို virtual ethernet devices ၂ခု လုပ်​ပေးသွားတာဖြစ်တယ်။ Host ရဲ့ network stack မှာ ip link command နဲ့​ခေါ်ကြည့်လိုက်ရင် interface ၂ခုလုံးကို​တွေ့နိုင်တယ်။ 

အဲ့​​တော့ကျွန်​တော်တို့လုပ်မယ့် သ​ဘောတရားက ကြိုးရဲ့ အစ တစ်ခုကို Host network ထဲမှာထားခဲ့မယ်။ ​နောက်အစ တစ်ခုကို ခုဏက container ရဲ့ namespace ထဲထည့်လိုက်မယ်။ ဒါဆို network namespace ၂ခုကြား connection တစ်ခုရှိသွားပြီ ဆိုတာမြင်သာလာလိမ့်မယ်။ 

```
sudo ip link set ceth 0 netns netns0 
```
Host ​ပေါ်မှာကျန်ခဲ့တဲ့ interface ကို ip ​ပေးပြီး up လိုက်မယ်။ 
````
sudo ip link set veth0 up 

sudo ip addr add 172.18.0.11/16 dev veth0 
````
![host-veth-ip](/assets/img/setting_ip_for_veth0.PNG)

ပြီးရင် container network namespace ထဲပြန်ဝင်မယ် ပြီးရင် သူ့ထဲက interface ကို ip ​ပေးပြီး up လိုက်မယ်။ 

```
sudo nsenter --net=/var/run/netns/netns0
ip link set lo up
ip link set ceth0 up
ip addr add 172.18.0.10/16 dev ceth0
```
![ip-ceth0](/assets/img/ip_for_ceth0.PNG)
အချင်းချင်း ping ကြည့်မယ်။

```
ping 172.18.0.11 
```
![ping-to-host](/assets/img/ping_to_host.PNG)

exit လုပ်ပြီး root network namespace ထဲပြန်သွားမယ်။ ဒီက​နေ container ထဲလှမ်း ping ကြည့်ရင်လည်း success ဖြစ်တာ​တွေ့နိုင်တယ်။ 
```
ping 172.18.0.10 
```
![ping_from_host](/assets/img/pingtonetns0fromhost.PNG)

Root network namespace မှာရှိတဲ့ တစ်ခြား interface ကို ပဲဖြစ်ဖြစ်၊ internet ​ပေါ်က တစ်ခြား ip ​တွေကို container ထဲက ping မယ်ဆိုရင် network unreachable ဖြစ်လိမ့်မယ်။ 

![ping_to_internet](/assets/img/ping_to_internet.PNG)

ဒါက​တော့ ဘာလိုလဲဆိုရင် သူ့မှာ route မရှိလို့ပဲဖြစ်တယ်။  
![route_table](/assets/img/route_table_of_netns0.PNG)

ဒါကိုဘယ်လိုလုပ်ရမလဲ ဆိုတာကို ​နောက်​နေ့မှာဆက်​ရေးသွားပါမယ်။

ဒီပို့စ်ကို​တော့ ကျွန်​တော် ​အောက်က blog က​​နေ စာဖတ်ရင်း refrence ယူပြီး​ရေးထားတာဖြစ်ပါတယ်။ original ကိုသွားဖတ်လို့လည်းရ​အောင် link ထည့်​ပေးထားပါတယ်။
[Original Post](https://iximiuz.com/en/posts/container-networking-is-simple/)
