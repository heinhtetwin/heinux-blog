---
layout: post
title: Introduction to Linux CLI
share-img: /assets/img/architecture-of-linux.png
thumbnail-img: /assets/img/architecture-of-linux.png
tags: [Linux,System Administration]
---

𝐋𝐢𝐧𝐮𝐱 𝐂𝐋𝐈 ဘာလဲ ဘယ်လဲ??

ဒီ​နေ့မှာ​တော့ကျွန်​တော်က Linux CLI ( Command line Interface ) ဆိုတာဘာလဲ ဆိုတာရယ်၊ GUI (Graphical User Interface ) ဆိုတာဘာလဲရယ်၊ CLI ကိုအသုံးပြုပြီး ဘာ​တွေပြုလုပ်လို့ရသလဲဆိုတာကို အတိုချုပ်​ပြောပြသွားပါမယ်။ 

✅𝐖𝐡𝐚𝐭 𝐢𝐬 𝐋𝐢𝐧𝐮𝐱 𝐊𝐞𝐫𝐧𝐞𝐥? 

ကျွန်​တော် Linux ဆိုတာဘာလဲဆိုတာကို မိတ်ဆက်ပို့စ်မှာတုန်းက Operating system (OS) လို့​ပြောခဲ့ပါတယ်။ ဒါက အလွယ်​ပြောလိုက်တာပါ။ တစ်ကယ်တမ်း​တော့ Linux ဆိုတာ kernel ပါ။ အို​ကေ..အဲ့​တော့ kernel ဆိုတာက​ကောဘာလဲ?? Kernel ကိုအလွယ်ဆုံး​ပြောရရင် kernel က OS မှာရှိတဲ့ User space နဲ့ hardware ကြားက ကြားခံ layer လို့​ပြောလို့ရပါတယ်။ e.g. User တစ်​ယောက် run ထားတဲ့ program တစ်ခုက memory ယူသုံးချင်တာမျိုး၊ file and directory access လုပ်ချင်တာမျိုးဆို OS နဲ့  interact လုပ်ဖို့ အတွက်ကို System call က​နေတစ်ဆင့်သွားရပါတယ်။ အဲ့လို user program က OS ရဲ့ Kernel ကို resources သုံးဖို့လှမ်း request လိုက်တာကို system call တစ်ခု​ခေါ်လိုက်တယ်လို့ သတ်မှတ်ပြီး အဲ့ system call success ဖြစ်မှ (exit code 0) နဲ့ပြန်လာမှ အဲ့ program က resources သုံးဖို့ခွင့်ပြုချက် ရမှာဖြစ်ပါတယ်။ စစချင်းမှာ​တော့ဒါ​တွေက ရှုပ်သလိုရှိပါတယ်။ ဒါ​ပေမဲ့ OS ကိုသုံးဖို့​တော့ ဒါ​တွေသိဖို့မလိုပါဘူး။ ဒါက underlying မှာဘယ်လိုအလုပ်လုပ်လဲဆိုတာကို အတိုချုပ်​ပြောတာပါ။ အဲ့ Linux Kernel ​ပေါ်မှာမှ GNU project က software  ​တွေ libraries ​တွေနဲ့​ပေါင်းပြီး GNU/Linux Distributions ​တွေထွက်​ပေါ် လာတာပါ။ ဒါကိုအများစုက Linux OS ဆိုပြီးပဲ အလွယ်​ခေါ်လိုက်ကြတာ ဖြစ်ပါတယ်။ 

✅𝐖𝐡𝐚𝐭 𝐢𝐬 𝐚 𝐆𝐔𝐈? 

​နောက်တစ်ပိုင်းမှာ​တော့ GUI ( Graphical User Interface ) ဆိုတာဘာလဲ ​လေ့လာကြည့်​ရ​အောင်..
တစ်ကယ်​တော့ သူ့နာမည်မှာထဲကိုက ကျွန်​​တော်တို့လိုချင်တဲ့ အ​ဖြေကပါပြီး​​နေပါပြီ၊ GUI ဆိုတာ ကျွန်​တော်တို့ ( Users ) ​တွေကို ဒီ Computer Operating systems ​တွေနဲ့ လွယ်လွယ်ကူကူ ဆက်သွယ်ဖို့အတွက် visual indicators ​လေး​တွေနဲ့ထည့်​ပေးထားပြီး အဲ့ icons ​လေး​တွေကိုနှိပ်ပြီး interact လုပ်လို့ရတာကို ဆိုလိုပါတယ်။ ဥပမာအားဖြင့် file အသစ်​လေးတစ်ခု create ချင်တယ်ဆို right click နှိပ်ပြီး new folder ​​လေးတစ်ခု ​ဆောက်လိုက်တာမျိုး​​ပေါ့။ ဒါကို CLI က​နေပြီးလည်း command ရိုက်ပြီးလုပ်လို့ရပါတယ်။ အဲ့​တော့​မေးစရာရှိပါတယ်။ ဘာလို့ဒီ​လောက်လွယ်လွယ်ကူကူ လုပ်လို့ရ​နေတာကို အလုပ်ရှုပ်ခံပြီး terminal ကလုပ်မှာလဲ​ပေါ့၊ ဒါက​တော့သူ့အားသာချက်နဲ့သူ ရှိပါတယ်။ ​အောက်မှာ CLI ကိုရှင်းပြီးရင် CLI ကိုသုံးရတဲ့ benefits ​​တွေလည်းထည့်သွင်း​ပြောသွားပါမယ်။ များ​သောအားဖြင့်​တော့ personal desktop အဖြစ်သုံးကြတဲ့ Linux distros ​တွေမှာ GUI ပါပါတယ်။ ​နောက်တစ်ချက်အ​နေနဲ့ Linux မှာအသုံးများတဲ့ GUI desktop environment ​တွေက​တော့ GNOME နဲ့ KDE Plasma တို့ရှိပါတယ်။ မတူညီတဲ့ environments ​တွေ​ပေါ်လိုက်ပြီး ပုံစံ​လေး​တွေနည်းနည်း​ပြောင်းပါတယ်။ ကိုယ်ကြိုက်တဲ့ favorite ဖြစ်တဲ့ Desktop environment ကို​ပြောင်း install လုပ်ပြီးသုံးလို့လည်း ရပါတယ်။ 

✅𝐖𝐡𝐚𝐭 𝐢𝐬 𝐚 𝐂𝐋𝐈?

အို​ကေ..ကျွန်​တော်တို့အဓိက​ပြောချင်တဲ့ CLI ဆိုတာဘာလဲလာပြီ။ CLI ( Command Line Interface ) ဆိုတာက​တော့ GUI လိုပဲ users ​တွေကို OS နဲ့ interact လုပ်နိုင်​အောင်လုပ်​ဆောင်​ပေးတဲ့ interface တစ်ခုပဲ၊ ဒါ​ပေမဲ့ သူ့မှာက graphical icons ​တွေမပါပဲ text only ပဲရိုက်လို့ရမှာ ဖြစ်တယ်။ အဲ့အတွက်​ကြောင့် ကျွန်​တော်တို့က CLI က​နေ ကျွန်​တော်တို့ desktop ကြီးကို တစ်ခုခုခိုင်းချင်တယ်ဆိုရင် သုံးရမယ့် command ကို​သေချာသိဖို့လိုတယ်၊ command မမှန်ရင်ဘာအလုပ်မှ လုပ်မှာမဟုတ်တဲ့ အတွက်ပဲဖြစ်တယ်။ 

✅𝐖𝐡𝐚𝐭 𝐢𝐬 𝐚 𝐓𝐞𝐫𝐦𝐢𝐧𝐚𝐥?

ဟုတ်ပြီ အဲ့​တော့ကျွန်​တော်တို့ Linux စသုံးရင်ကြားဖူး​နေတာ ရှိမယ်၊ Terminal ဆိုတဲ့စာလုံး​ပေါ့၊ အဲ့​​တော့ Terminal နဲ့ CLI ကတူတူပဲလား ဘယ်လိုလဲ​ပေါ့၊ တစ်ကယ်​တော့ Terminal ဆိုတာ User တစ်​ယောက်က CLI environment သုံးပြီး OS နဲ့ interact လုပ်လို့ရ​အောင် ပြုလုပ်​ပေးတဲ့ IDE တစ်ခုလို့​ပြောလို့ရပါတယ်။ ကျွန်​တော်တို့က GUI ပါတဲ့ Linux distro သုံး​နေရင်းနဲ့လည်း terminal window ​လေးတစ်ခုဖွင့်ပြီး command ရိုက်လို့ရသလို​ပေါ့။ အဲ့လို terminal က​နေကျွန်​​တော်တို့ ရိုက်ထည့်လိုက်တဲ့ commands ​တွေကို​နောက်က​နေ တစ်ကယ် execute လုပ်​ပေးတာက​တော့ shell ပါ။ အဲ့​တော့ shell အ​ကြောင်းဆက်သွားလိုက်ရ​အောင်.. 

✅𝐖𝐡𝐚𝐭 𝐢𝐬 𝐚 𝐒𝐡𝐞𝐥𝐥? 

Shell ဆိုတာဘာလဲ ဆိုတာကိုအတို​ကောက် ​ပြောရရင်​တော့ command line interpreter တစ်ခုလို့​ပြောရပါမယ်။ Shell ကဘယ်မှာရှိလဲဆို​တော့ Kernel နဲ့ users ​တွေရဲ့ကြားမှာရှိပါတယ်။ ဆိုလိုချင်တာသည် ကျွန်​​တော်တို့ terminal ကရိုက်လိုက်တဲ့ command တစ်ခု  (e.g. ls ) ဆိုပါ​တော့၊ အဲ့ text ​လေးဝင်လာတဲ့အခါမှာ shell ကဒီ command ဟာတစ်ကယ် system ထဲမှာ binary file ရှိလားဆိုတာကို သူ့ရဲ့သတ်မှတ်ထားတဲ့ directories ​တွေမှာစစ်မယ်၊ အကယ်၍ ရှိတယ်ဆိုရင် သူက အဲ့ executable file ကို execute လုပ်လိုက်မယ်၊ ထွက်လာတဲ့ output ကိုမှ ကျွန်​​တော်တို့ (users) ​တွေကို terminal မှာပြန်လာပြ​​ပေးတာဖြစ်တယ်။ အဲ့မှာမှ users က command မှာ typo ပါတာတို့ဘာတို့ဆို shell ကသိပြီး user ဆီကို error message ပြန်ပြ​ပေးလိမ့်မယ်။ Shell မှာလည်း အမျိုးအစား ကွဲတာ​တွေ အများကြီးရှိပြီး အစပိုင်းမှာ sh ( Bourne shell ) ကိုအသုံးပြုခဲ့ကြပြီး ​နောက်ပိုင်းမှာသူ့ကို modified လုပ်ထားတဲ့ Bash ( Bourne Again Shell ) ကိုအသုံးများလာခဲ့ကြပါတယ်။ တစ်ခြား Windows မှာ နာမည်ကြီးတဲ့ PowerShell လိုမျိုး​တွေလည်း ရှိပါ​သေးတယ်။ ဒီ shell ​တွေကိုသုံးပြီး ကျွန်​တော်တို့က administrative purposes ​တွေအတွက် shell scripts ​တွေလည်းဖန်တီးလို့ရပါ​သေးတယ်။ 

✅𝐁𝐞𝐧𝐞𝐟𝐢𝐭𝐬 𝐚𝐧𝐝 𝐝𝐫𝐚𝐰𝐛𝐚𝐜𝐤𝐬 𝐨𝐟 𝐂𝐋𝐈 

အဲ့​တော့ CLI မှာ​ကောင်းကျိုး​တွေကြီးပဲလား၊ သူ့ကိုသုံးရင် ဘာ drawbacks ​တွေရှိလဲဆိုတာ ကြည့်ကြည့်ရ​အောင်.. 

🔶🔶ပထမဆုံး အ​နေနဲ့​တော့ GUI ကိုမသုံးပဲ CLI ကိုသုံးရင် ကျွန်​တော်တို့ စက်မှာရှိတဲ့ memory (RAM) စားတာသက်သာပါတယ်။ GUI မှာ graphical components ​တွေအများကြီးသုံးထားတာ​​ကြောင့်ပါ။ 

​🔶🔶နောက်တစ်ချက်က​တော့ CLI ကိုသုံးပြီး command run လိုက်တာဟာ GUI သုံးတာထက် သိသိသာသာ ပိုမြန်ပါတယ်။ 

🔶🔶ဒါ​ပေမဲ့ စစချင်းသုံးမယ့် user တစ်​ယောက်အတွက်ဆိုရင်​တော့ CLI သုံးဖို့က သိပ်လွယ်ကူမှာမဟုတ်ပါဘူး။ commands ​တွေသိဖို့လိုအပ်တာ​ကြောင့် ဖြစ်ပါတယ်။ 

​🔶🔶နောက်ဆုံးတစ်ချက်က​တော့ GUI ကိုသုံးမယ်ဆို ကိုယ်ကြိုက်သလို appearance ​ကို customize လုပ်လို့ရပြီး CLI မှာ​တော့အဲ့လိုမရပါဘူး။ 

ဒီ​တော့ကိုယ့်ရဲ့လိုအပ်ချက်​ပေါ်မူတည်ပြီး CLI နဲ့ သုံးမှာလား၊ GUI နဲ့သုံးမှာလား ဆိုတာကို​​ရွေးချယ်ရမှာပဲ ဖြစ်ပါတယ်။ Resource Management အ​ရေးကြီးတဲ့ server ထိုင်မှာမျိုးတို့လို့​နေရာမှာဆို CLI ကပိုသင့်​တော်ပြီး ကိုယ့် laptop ​လေးထဲမှာပဲ ထည့်သုံးချင်တာဆိုရင်​တော့ GUI နဲ့လည်းအဆင်​ပြေပါတယ်။ ကိုယ်က commands ​တွေလည်းသိတယ်၊ VM ကိုလည်း resource အများကြီး မ​ပေးချင်ဘူးဆိုရင်​တော့ CLI သုံးလည်း ရပါတယ်။ 

ဒီ​နေ့မှာ​တော့ ကျွန်​တော်က Linux မှာ ရှိတဲ့ CLI နဲ့ GUI အ​ကြောင်းကို အကျဥ်းချုပ် ​ပြောခဲ့ပြီး​တော့ knowledge လည်းရမယ်လို့​မျှော်လင့်ပါတယ်။ ​နောက်ရက်​တွေမှာ​တော့ ဒီ Linux CLI ကိုသုံးတဲ့​နေရာမှာ အသုံးဝင်တဲ့ commands ​လေး​တွေအ​ကြောင်းနဲ့ useful options ​တွေနဲ့ ဘယ်လိုတွဲသုံးရမလဲ ​ပြောပြ​ပေးသွားပါမယ်။ 
​ဖတ်​ပေးတဲ့အတွက် ကျေးဇူးတင်ပါတယ်။

𝓗𝓮𝓲𝓷𝓾𝔁 𝓑𝓵𝓸𝓰
