---
layout: post
title: How does Linux handle software packages?
tags: [Linux,System Administration]
---
 
ဒီ​​နေ့မှာ​တော့ ကျွန်​တော်က Linux မှာ software ​တွေကို ဘယ်လိုနည်း​တွေနဲ့ install လုပ်လို့ရလဲ၊ ပြီး​​တော့ software packages ​တွေဘာ​တွေရှိလဲဆိုတာကို ရှင်းပြသွားပါမယ်။ ကဲစလိုက်ရ​အောင်... 

## 𝐖𝐡𝐚𝐭 𝐢𝐬 𝐚 𝐩𝐚𝐜𝐤𝐚𝐠𝐞?


ပထမဆုံးအ​နေနဲ့ package ဆိုတာဘာလဲ ကိုသိဖို့လိုအပ်ပါတယ်။ အလွယ်​ပြောရရင်​တော့ Linux မှာ software package တစ်ခုဆိုတာ အဲ့ software ကို ကိုယ့်ရဲ့ pc or laptop ထဲမှာထည့်ပြီး အသုံးပြုနိုင်ဖို့အတွက် လိုအပ်တဲ့ dependencies ​တွေ data ​တွေ libraries ​တွေကို​ပေါင်းပြီး archive and compress လုပ်ထားတဲ့ zip file တစ်ခုလို့​ပြောလို့ရပါတယ်။ Windows မှာဆို ကျွန်​တော်တို့ app တစ်ခု သွင်းချင်တယ်ဆို vendor ရဲ့ website က​နေ .exe file ​လေးသွား download ဆွဲပြီး install လုပ်သလို​ပေါ့၊ Linux မှာလည်း အဲ့လိုမျိုးသွင်းဖို့အတွက် binary package ဆိုတာရှိပါတယ်။ ဒါ​ပေမဲ့ တစ်ခုထူးခြားတာက Linux မှာ source package က​နေလည်း install လုပ်လို့ရပါ​သေးတယ်။ ​အောက်မှာသူတို့ ၂ခုရဲ့ ကွဲပြားပုံကိုဆက်​ပြောသွားပါမယ်။ 

## 𝐁𝐢𝐧𝐚𝐫𝐲 𝐩𝐚𝐜𝐤𝐚𝐠𝐞𝐬 𝐯𝐬 𝐬𝐨𝐮𝐫𝐜𝐞 𝐩𝐚𝐜𝐤𝐚𝐠𝐞𝐬 


အရင်ဆုံး Binary package ဆိုတာဘာလဲဆိုတာ မ​ပြောခင် ဒီ packages ​တွေကဘယ်မှာရှိ​နေတာလဲ ဆိုတာကိုအရင်​ပြောပါမယ်၊ Linux မှာ သူ့ရဲ့သက်ဆိုင်ရာ distros ​တွေကသုံးတဲ့ software repository ​တွေရှိပါတယ်။ အဲ့ repo ​တွေက​​​နေကျွန်​တော်တို့က CLI က​နေ package manager ​တွေသုံးပြီးဖြစ်ဖြစ် GUI မှာဆိုရင် Linux app store ​တွေသုံးပြီးဖြစ်ဖြစ် download and install လုပ်လို့ရမှာဖြစ်ပါတယ်။ ဒါကိုသိပြီဆို Binary package တစ်ခုဆိုတာဘာလဲဆိုတာ​​လေ့လာလိုက်ရ​အောင်၊ ပုံမှန်အားဖြင့် မတူညီတဲ့ Linux distros ​တွေက သူတို့ရဲ့ OS ​တွေနဲ့ကိုက်ညီ​အောင် pre-built ပြုလုပ်​ပေးထားပြီး files အကုန်လုံးကို archive format နဲ့ ထုတ်​ပေးထားတာကို binary package တစ်ခုလို့ ​ခေါ်ပါတယ်။ Binary package မှာဘာ​တွေပါလဲဆို​တော့ source code တစ်ခုကို machine နားလည်​အောင် compile လုပ်ထားပြီးသား executable file နဲ့ လိုအပ်တဲ့ configuration files ​တွေပါပါတယ်။ တစ်ချက်ရှိတာက​တော့ binary packages ​တွေက pre-compiled pre-built လုပ်​ပေးထားတာဖြစ်လို့ သူတို့သက်ဆိုင်ရာ architecture (e.g. x86) ဆိုအဲ့ architecture ရှိတဲ့ machines ​တွေ​ပေါ်မှာပဲ run လို့ရမှာဖြစ်ပါတယ်။ Binary packages ​တွေကိုသုံးလို့ရတဲ့ အားသာချက်​က​တော့ ကိုယ်က manual compile လုပ်စရာမလိုတဲ့အတွက် သုံးရလွယ်ကူပြီး ​နောက်တစ်ချက်က ​နောက်ပိုင်း install လုပ်ထားပြီးသား program ​တွေကို update လုပ်တဲ့အခါ​တွေမှာလည်း package manager က​နေလုပ်လို့ရတာဖြစ်လို့ ပိုပြီးလွယ်ကူပါတယ်။ 

## 𝐈𝐧𝐬𝐭𝐚𝐥𝐥𝐢𝐧𝐠 𝐟𝐫𝐨𝐦 𝐬𝐨𝐮𝐫𝐜𝐞 𝐩𝐚𝐜𝐤𝐚𝐠𝐞 


Source packages ​တွေက​တော့ binary packages ​တွေနဲ့မတူပါဘူး၊ ဘာမတူတာလဲဆို​တော့ သူတို့က source code ပဲပါဝင်တာဖြစ်ပါတယ်။ ဒါ့​​​ကြောင့်သင်ကသာ မှန်မှန်ကန်ကန် compile လုပ်နိုင်တယ်ဆို ဘယ် machine ​ပေါ်မှာမဆို run လို့ရ​အောင် ပြုလုပ်နိုင်မှဖြစ်ပါတယ်။ တစ်ခုရှိတာက​တော့ သင်ကိုယ်တိုင် အဲ့ package မှာပါတဲ့ documentation ကိုဖတ်ပြီး manual install လုပ်ရမှာပါ၊ ဥပမာ အားဖြင့် ကိုယ်သွင်းချင်တဲ့ program ကဘာ dependencies ​တွေရှိလဲ၊ အဲ့တာ​တွေကိုရှာပြီး ကိုယ့်စက်​ပေါ်မှာ လိုအပ်တဲ့ libraries ​တွေရှိ​နေ​အောင်ပြုလုပ်ထားဖို့လိုပါတယ်။
​နောက်ပြီး program ရဲ့ source code ​ပေါ်မူတည်ပြီး ကိုက်ညီတဲ့ compiler tools ​တွေနဲ့ compile လုပ်​ပေးရပါမယ်။ ဥပမာ အားဖြင့် C, C++ languages ​တွေနဲ့​ရေးထားတယ်ဆို GCC compiler သုံးပြီး machine နားလည်တဲ့ binary file တစ်ခုဖြစ်​အောင်လုပ်​ပေးရပါမယ်။ ​နောက်ထပ်အသုံးဝင်တဲ့ tool က​တော့ make ပဲဖြစ်ပါတယ်။ သူက​တော့ အ​ပေါ်မှာ​ပြောခဲ့တဲ့ compile နဲ့ build လုပ်တဲ့ process ကို automate လုပ်​ပေးတာဖြစ်ပါတယ်။ make command ဘယ်လိုအလုပ်လုပ်လဲ​တော့ အ​သေးစိပ်မ​ရေး​တော့ပါဘူး။ စိတ်ဝင်စားရင်လာ discuss လုပ်နိုင်ပါတယ်။ Source packages ​တွေကို အသုံးပြုလို့ရတဲ့ အားသာချက်က​တော့ program ​တွေ install လုပ်တဲ့​နေရာမှာ ကိုယ်ကြိုက်သလို customize လုပ်လို့ရတဲ့အတွက် ကိုယ်မလိုချင်တဲ့ features ​တွေရှိရင်မထည့်​တော့ပဲ program ကို weight ​လျှော့လို့ရပါတယ်။ 

## 𝐒𝐨𝐟𝐭𝐰𝐚𝐫𝐞 𝐫𝐞𝐩𝐨𝐬𝐢𝐭𝐨𝐫𝐲 


ကျွန်​တော် အ​ပေါ်မှာ​ပြောခဲ့သလိုပါပဲ၊ မတူညီတဲ့ Linux distributions ​တွေက မတူညီတဲ့ software repositories ​တွေကိုအသုံးပြုပါတယ်။ software repository ဆိုတာက​တော့ ဒီ program binary archive files ​တွေသွား download ဆွဲလို့ရတဲ့ URL တစ်ခု​ပါ။ RedHat ​အတွက်သူ​ထောင်ထားတဲ့ repository ရှိသလို Debian မှာလည်း သူ​ထောင်ထားတဲ့ repository ရှိပါတယ်။ တစ်ချို့ distributions ​တွေက​တော့ ကိုယ်ပိုင်သပ်သပ်ရယ်လို့မရှိပဲ ခွဲသုံးပါတယ်။ ဥပမာအားဖြင့် ubuntu က Debian ရဲ့ repository တစ်ချို့ကိုသုံးပါတယ်။ ​နောက်​နေ့မှာ​​တော့ ဒီ software repositories ​တွေကို Linux OS က​နေ ဘယ်လို package manager ​တွေသုံးပြီး access သွားလုပ်လို့ရလဲဆိုတာ​ပြောသွားပါမယ်။ 

​ကျေးဇူးတင်ပါတယ်။ 
