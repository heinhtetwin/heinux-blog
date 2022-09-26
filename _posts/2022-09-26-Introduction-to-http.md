---
layout: post
title: History of http and improvements
share-img: /assets/img/HTTP_intro.png
thumbnail-img: /assets/img/HTTP_intro.png
tags: [Web]
---

ကဲ Linux linux နဲ့ ဒါ​တွေကြီးပဲကြည့်​နေရတာ ပျင်းလာပြီလား? ဒီ​နေ့မှာ​တော့ http protocol နဲ့ပတ်သက်တဲ့ knowledge sharing တစ်ခုလုပ်​ပေးချင်ပါတယ်။ 

𝙒𝙝𝙖𝙩 𝙞𝙨 𝙝𝙩𝙩𝙥?

ပထမဆုံးအ​နေနဲ့ http ဆိုတာဘာလဲဆိုတာအရင်​ပြောကြည့်ရ​အောင်၊ စာ​ရေးသူတို့ websites ​တွေ ဖွင့်ကြည့်တဲ့အခါမှာ chrome or mozila or တစ်ခြားဘယ် browser မှာပဲဖြစ်ဖြစ် အ​ပေါ်ကဘားတန်း​လေးကို​ထောက်ကြည့်လိုက်မယ်ဆိုရင် ​ရှေ့ဆုံးက http or https နဲ့အစပြုတာကို​တွေ့ရပါတယ်။ ပုံမှန်ကျွန်​တော်တို့သုံး​နေတဲ့ sites ​တွေအကုန်လုံးမှာ​တော့ https ကိုပဲ​တွေ့ရလိမ့်မယ်ထင်ပါတယ်။ ဒါကဘာလို့လဲဆို​တော့ https ဟာ http ထပ်ပိုပြီး security perspective အရပို​ကောင်းလို့ ယ​နေ့​ခေတ်မှာ https ကိုပဲ web applications ​တွေကသုံးကြတယ်လို့မှတ်ထားနိုင်ပါတယ်။ အို​ကေအဲ့​တော့လိုရင်းကို ဆက်သွားလိုက်ကြရ​အောင်.. စာ​ရေးသူခု mention လုပ်​နေတဲ့ http ဆိုတာကို communication protocol တစ်ခုလို့အဓိပ္ပယ်ဖွင့်ပါတယ်။ ဆိုလိုတာက ကျွန်​တော်တို့ users ​တွေဟာ ဒီ websites ​တွေ web applications ​တွေကို သုံးတဲ့​နေရာမှာ server ဘက်က data ​တွေကို ကိုယ့်ဆီမှာလာမြင်ရဖို့အတွက် communication လုပ်မဲ့နည်းလမ်းတစ်ခုလိုလာပါတယ်။ ဒီ​နေရာမှာကျွန်​တော်တို့က http ဆိုတဲ့ အရာဝင်လာတာဖြစ်ပါတယ်။ သ​ဘောက​တော့ client နဲ့ server ကြားမှာ communicate လုပ်မဲ့ standard definitions ​တွေကိုသတ်မှတ်​ပေးလိုက်တာပါ။ ဒါ​ပေမယ့် ဒီ websites ​နဲ့ users ကြားမှမဟုတ်ပါဘူး။ ဒီ applications ​တွေအချင်းချင်းကြားမှာ ဆက်သွယ်ဖို့ API လို့​ခေါ်တဲ့ Application Programming Interface ​တွေမှာလည်း http protocol ကိုအသုံးပြုပါတယ်။ 

𝘼 𝙡𝙞𝙩𝙩𝙡𝙚 𝙙𝙚𝙚𝙥 𝙙𝙞𝙫𝙚 𝙞𝙣𝙩𝙤 𝙝𝙩𝙩𝙥

အဲ့​တော့ဒီ http protocol မှာဘာ​တွေပါဝင်လဲတစ်ချက်ကြည့်ကြည့်ရ​အောင်၊ ကျွန်​တော်တို့အလွယ်ဆုံးအ​နေနဲ့ http protocol မှာ ​၄မျိုးပါဝင်တယ်လို့ သိထားနိုင်ပါတယ်။ 

1. Request method
2. Request URL
3. Request headers
4. Request body ဆိုပြီး​တော့ပါ။ 

မြင်သာ​အောင်ပုံ​လေးနဲ့တွဲပြပါမယ်။ 

![HTTP_reeust_format](/assets/img/http_request.jpg)

Method ဆိုတာက​တော့ ဒီ client က server ကိုလှမ်းပြီး connect တဲ့အချိန်မှာ ဘာရည်ရွယ်ချက်နဲ့လာတာလဲဆိုတာကို define တာပါ။ ဆိုလိုတာက Data ရယူချင်တာလား၊ update လုပ်ချင်တာလား၊ delete လုပ်ချင်တာလားဆိုတာကို ဒီ method နဲ့ကြည့်နိုင်ပါတယ်။ 
​နောက်တစ်ခု URL ဆိုတာက​တော့ ဒီ request ​တွေကို client ကဘယ် path ကို send လုပ်မှာလဲဆိုတာကို define တာပါ။ မြင်သာတာက​တော့ကျွန်​တော်တို့ browsers ​တွေမှာကြည့်ရင်အ​ပေါ်ဘားတန်း​လေးက စာ​ကြောင်းဟာ URL ပါပဲ၊ ဒါကို​တော့ general knowledge အသင့်အတင့်ရှိတဲ့လူတိုင်းသိပြီး ဖြစ်မယ်ထင်ပါတယ်။ 
Headers ဆိုတာက​တော့ communication လုပ်တဲ့အချိန်မှာ အသုံးပြုမယ့် types ​တွေကို define တာဖြစ်ပါတယ်။ ဆိုလိုတာက data ​တွေကို plain text နဲ့လိုချင်တာလား json format နဲ့လိုချင်တာလား၊ ဒီလိုမျိုးပါ။ 
Body မှာ​တော့ တစ်ကယ် ဒီ client ဆီက​နေ server ကို လှမ်းပို့မယ့် real data ​တွေပါဝင်ပါတယ်။ server ဆီက​နေလှမ်းပဲ​တောင်းချင်တာဖြစ်ပြီး ပို့မယ့် data မရှိရင် body မပါတဲ့ request လည်းရှိနိုင်ပါတယ်။ 
ဒီ​နေရာမှာ ရှိတဲ့ methods အ​ကြောင်း​တွေ၊ data type အမျိုးအစား​တွေကို အ​သေးစိပ်ထည့်​မ​ပြော​တော့ပါဘူး။ ကျွန်​တော်ဒီ​နေ့တစ်ကယ် share ချင်တာက http protocol ရဲ့ version ​တွေအ​ကြောင်းနဲ့ သူတို့တစ်ခုနဲ့တစ်ခု ဘယ်လိုကွာသွားလဲဆိုတဲ့အ​ကြောင်း​တွေဖြစ်ပါတယ်။ ​အောက်မှာပုံ​လေး​တွေနဲ့ တွဲကြည့်ပြီး version တစ်ခုချင်းစီရဲ့ အလုပ်လုပ်ပုံ​တွေ​ပြောင်းသွားတာကိုကြည့်နိုင်ပါတယ်။ 

𝙃𝙏𝙏𝙋/1.0

HTTP/1.0 မှာ​တော့ client က server ကို connect တဲ့​နေရာမှာ request တစ်ခုကို connection တစ်ခုအ​နေနဲ့ဆက်သွယ်ပါတယ်။ ဆိုလိုတာက ကျွန်​တော်တို့ http request တစ်ခုအတွက် http connection တစ်ခု established ဖြစ်ပြီး server ဘက်က​နေ response ကို​စောင့်ပါတယ်။ response ရပြီးသွားရင်​တော့ ဒီ http request process တစ်ခုပြီးသွားပြီလို့သတ်မှတ်ပြီး connection ပါ terminate ဖြစ်သွားပါတယ်။  ဆို​တော့ client က ​​နောက် request အသစ်တစ်ခုထပ်ပို့ချင်ရင် connection initiate အစက​နေပြန်လုပ်ရမှာဖြစ်ပါတယ်။

𝙃𝙏𝙏𝙋/1.1

HTTP/1.1 မှာ​တော့ HTTP/1.0 တုန်းကရှိခဲ့တဲ့ ချို့ယွင်းချက်​တွေကိုပြင်ဆင်ပြီး connection တစ်ခုထဲမှာပဲ multiple request ပို့နိုင်​အောင်ပြုလုပ်ခဲ့ပါတယ်။ ဆိုလိုတာက client နဲ့ server မှာ connection တစ်ခုရပြီးရင် ​နောက် client ဘက်ကဆက်ပို့မယ့် sub-sequent request ​တွေအတွက် connection အသစ်တစ်ခု established လုပ်စရာမလို​အောင် keep alive connection အ​နေနဲ့အသုံးပြုလိုက်တာ ဖြစ်ပါတယ်။ အဲ့တာရဲ့ အကျိုး​ကျေးဇူးက​တော့ web page ​တွေ loading လုပ်တဲ့ time က အရင် 1.0 ထက်သိသိသာသာ မြန်သွားမှာပဲဖြစ်ပါတယ်။ ​နောက်သိသိသာသာ ထပ် improvement ဖြစ်ခဲ့တာက​တော့ version 1.0 မှာမရခဲ့တဲ့ PUT, PATCH နဲ့ DELETE method ​တွေကိုပါ ထပ်ထည့်​ပေးခဲ့ပါတယ်။ ယ​နေ့​ခေတ်မှာလည်း အသုံးအများဆုံး version က HTTP/1.1 လို့​ပြောလို့ရပါတယ်။

![http1_vs_1.1](/assets/img/http1_vs_1.1.jpg)

𝙃𝙏𝙏𝙋/2 

HTTP/2 မှာလည်းထိုနည်းတူစွာပဲ အရင် version 1.1 ထက်ပို​ကောင်း​အောင် improvement ​တွေအများကြီးလုပ်ခဲ့ပါတယ်။ အဲ့ထဲကမှ အထင်သာဆုံးတစ်ချို့အချက်​တွေကို​ပြောသွားပါမယ်။

✅ Header compression - HTTP/1.1 မှာတုန်းက ကျွန်​တော်တို့ဟာ requests ​တွေ response ​တွေမှာပါတဲ့ headers ​တွေကို plain text အ​နေနဲ့သာ​ပေးပို့ခဲ့ကြပါတယ်။ HTTP version 2 မှာ​တော့ binary framing layer တစ်ခုကိုအသုံးပြုပြီး headers ​တွေမှာ plain text အစား compressed လုပ်ထားတဲ့ data ​တွေကိုပဲ​ပေးပို့သွားပြီး client ဘက်​ရောက်မှ ပြန်ပြီး decompress လုပ်တဲ့ approach ကိုသုံးသွားပါတယ်။ အဲ့လို​ပြောင်းလိုက်တဲ့အတွက်​ကြောင့် web page loading time မှာသိသိသာသာ ​လျော့နည်းသွားပါတယ်။ ဘာလို့လဲဆို​တော့ data ​တွေကို compress လုပ်ပြီးပို့တာဖြစ်တဲ့အတွက် network traffice မှာမလိုအပ်ပဲ usage ​တွေမများ​တော့ပါဘူး။ 

✅ Multiplexing - အရင် version 1.1 မှာတုန်းက sub sequent request ပို့လို့ရသွားတယ်ဆို​ပေမဲ့ sequentially ပဲပိုလို့ရခဲ့ပါတယ်။ ဆိုလိုတာက client တစ်​ယောက်က request တစ်ခုစပို့ပြီး ​နောက်တစ်ခုပို့ချင်တယ်ဆိုရင် ပထမပို့ခဲ့တဲ့ request က response ရပြီးမှသာ​နောက်တစ်ခုထပ်ပို့လို့ရမှာပါ။ ဒါကို technology term အရ Head-of-line blocking လို့ညွှန်းဆိုပါတယ်။ HTTP/2 မှာ​တော့ အဲ့ flow ကို change ခဲ့ပြီး sub sequent request ​တွေကို asynchronously ပို့လို့ရ​စေ ခဲ့ပါတယ်။ Request ​နောက်တစ်ခုပို့ဖို့အတွက် ပထမ request အဆုံးထိပြီးစရာမလိုပါဘူး။ ဒီလို request ​တွေ asynchronous ပို့လို့ရတာကို technology term အရ multiplexing လို့​ခေါ်ပါတယ်။ ​

✅ Stream prioritization - နောက် သိသိသာသာ version 2 မှာ change ခဲ့တာက​တော့ request stream ​တွေကို priority သတ်မှတ်​ပေးလို့ရသွားပါတယ်။ ဆိုလိုတာက client က​ပေးပို့လိုက်တဲ့ asynchronous requests ​တွေမှာ ဘယ် request ကို priority ထားပြီး response အရင်ပြန်ရမလဲဆိုတာမျိုးပါ။

![http1.1_vs_2](/assets/img/http1.1_vs_2.jpg)

𝙃𝙏𝙏𝙋/3 

နောက်ဆုံးအ​နေနဲ့ ​ပြောသွားမှာက​တော့ HTTP/3 အ​ကြောင်းပဲဖြစ်ပါတယ်။ HTTP/3 ကို 2020 မှာ စတင်မိတ်ဆက်ခဲ့ပါတယ်။ HTTP 3 မှာအရင် http versions ​တွေနဲ့အဓိက ကွာသွားတဲ့အချက်က​တော့ ​အောက်က underlying ဖြစ်တဲ့ layer4 transport layer မှာပဲဖြစ်ပါတယ်။ အရင် http versions ​တွေတုန်းက ကျွန်​တော်တို့ဟာ HTTP-over-TCP ဆိုတဲ့ ပုံစံမျိုးကိုပဲ အသုံးပြုခဲ့ကြပြီး ဒီ version3 မှာ​တော့ QUIC ဆိုတဲ့ protocol ကို​ပြောင်းလဲအသုံးပြုခဲ့ပါတယ်။ QUIC ဆိုတာက Quick UDP Internet Connection ရဲ့အတို​ကောက်ဖြစ်ပြီး UDP protocol ​ပေါ်မှာပဲ အ​ခြေခံထားတာပါ။ Networking အ​​ခြေခံကို​လေ့လာဖူးတဲ့ သူ​တွေဆိုရင်​တော့ သိပါလိမ့်မယ်၊ TCP က statefeul protocol ဖြစ်ပြီး UDP က​တော့ stateless ဖြစ်ပါတယ်။ ဆိုလိုတာက TCP connection တစ်ခု established ဖြစ်ဖို့ဆိုရင် tcp three way handshake ပြုလုပ်ပြီးမှ client နဲ့ server အချင်းချင်း data ​ပေးပို့လို့ရမှာပါ။ UDP မှာ​တော့အဲ့လိုမဟုတ်ပဲ client ကပို့ပြီးရင်ပြီးပါပြီ၊ server ဘက်က acknowledgement ကိုသူစိတ်မဝင်စားပါဘူး။ HTTP/2 မှာတုန်းက secured connection ဖြစ်ဖို့အတွက် TCP connection ​ပေါ်မှာမှ TLS handshake ထပ်ပြုလုပ်ရပါတယ်။ QUIC မှာ​တော့ secured connection ရဖို့အတွက် single handshake ပဲအသုံးပြုတာ​ကြောင့် စတင် connection initate လုပ်တဲ့ time ဟာ သိသိသာသာ​လျော့ကျသွားမှာပါ။ ​နောက်တစ်ချက်က​တော့ HTTP/2 မှာတုန်းက multiplexing ကို support ​ပေးခဲ့တယ်ဆို​ပေမယ့် ဒီ connection streams ​တွေထဲက stream တစ်ခုခုမှာ data loss ဖြစ်သွားရင် အကုန်အစက ပြန်ပို့ရပါတယ်။ Version3 မှာ​တော့ ဒီ issue မရှိ​တော့ပဲ အကယ်၍ stream တစ်ခုခုမှာ data loss ဖြစ်ခဲ့ရင် အဲ့ loss ဖြစ်သွားတဲ့အပိုင်းကိုပဲ ဖြတ်ပြီးပြန်ပို့မှာဖြစ်ပါတယ်။ ​​နောက်ဆုံးအချက်အ​နေနဲ့ က​တော့ HTTP/3 ဟာ secured connection နဲ့ပဲ support ​ပေးတာဖြစ်ပြီး အရင်က version 1 ​တွေ 2 ​တွေမှာ​တော့ TLS handshake မပါတဲ့၊ https ကိုမသုံးပဲ ရိုးရိုး http type နဲ့လည်း web servers ​တွေကို implement လုပ်လို့ရခဲ့တာပဲ ဖြစ်ပါတယ်။

![http2_vs_3](/assets/img/http2_vs_3.jpg)

ဒီ​နေ့မှာ​တော့ စိတ်ကူး​ပေါက်တဲ့အတိုင်း http protocol အ​ကြောင်းနဲ့ history အ​ကြောင်း​တွေကို​ပြောဖြစ်ခဲ့တာပါ။ ကျွန်​တော်က​တော့ ဘယ်ဟာမဆို ဘာသာရပ်တစ်ခုခုကို ​လေ့လာ​တော့မယ်ဆိုရင် ကျွန်​တော့်ရဲ့ အမြင်မှာ​တော့ နဂိုအရင်က ဒါ​တွေကိုဘယ်လိုသုံးခဲ့တယ်၊ ပြီး​တော့ယခုလက်ရှိ အချိန်မှာ​ရော ဘယ်လိုသုံး​နေတယ် ဆိုတာကို တွဲ​လေ့လာဖြစ်ပါတယ်။ ဒါမှသာ အရင်ကဘယ်လို weakness ​တွေရှိခဲ့လို့ ဒါ​တွေကိုပြင်ဆင်ရင်းအခုအချိန်မှာ ဘယ်လို technology ကတိုးတက်လာတယ်ဆိုတာကို မြင်သွားမှာဖြစ်ပြီး ဒီဘာသာရပ်ကိုလည်း စိတ်ဝင်တစ်စား ဆက်လက်​လေ့လာဖြစ်မှာလို့ ထင်တဲ့အတွက်​ကြောင့်ဖြစ်ပါတယ်။ ဒါက​တော့ စာ​လေ့လာ​နေတဲ့သူ​တွေကို ကျွန်​တော်ရဲ့ personal အကြံဥာဏ်​လေး​ပေးချင်တာပါ၊ တစ်ခြားအမြင်မတူတာမျိုး​တွေလည်းရှိနိုင်ပါတယ်။ ကိုယ်​ခေါင်းထဲ အ​ရောက်ဆုံးလို့သတ်မှတ်တဲ့ ​လေ့လာမှူမျိူးကသာ ကိုယ့်အတွက်​အ​ကောင်းဆုံးပါ။

