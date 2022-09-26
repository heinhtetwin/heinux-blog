---
layout: post
title: Process Life Cycle in Linux
share-img: /assets/img/process_life_cycle.png
thumbnail-img: /assets/img/process_life_cycle.png
tags: [Linux,System Administration]
---

ကဲ ဒီ​နေ့မှာလည်း Linux နဲ့ပတ်သက်တဲ့ under the hood ထဲက process ​တွေအလုပ်လုပ်ပုံကို ဆက်လက်​ပြောသွားပါမယ်။ ဒီပို့စ်မှာ​တော့ Process တစ်ခုရဲ့ စတင် create လုပ်လိုက်တဲ့အချိန်ကစပြီး အဆင့်ဆင့်ဖြတ်သန်းရတဲ့ different states ​တွေ၊ ဒီ process ​တွေအချင်းချင်း communicate ဘယ်လိုလုပ်လဲ ဆိုတာ​တွေ ထည့်​ပြောဖြစ်ပါတယ်။ 

𝑫𝒊𝒇𝒇𝒆𝒓𝒆𝒏𝒕 𝒔𝒕𝒂𝒕𝒆𝒔 𝒐𝒇 𝒂 𝒑𝒓𝒐𝒄𝒆𝒔𝒔

ကျွန်​တော်တို့​တွေဟာ system ​တစ်ခုကို စ power on လိုက်ပြီဆိုတာနဲ့ OS က​နေသူ့ အလိုအ​လျှောက် start လုပ်သွားတဲ့ process ​တွေရှိသလို user က run ချင်လို့ ရည်ရွယ်ချက်ရှိရှိ စ run လိုက်တဲ့ process ​တွေလည်းရှိပါတယ်။ သို့​သော် ဘယ်လိုပင်ဖြစ်ဖြစ် process တစ်ခု စပြီဆိုတာနဲ့ ဒီ process ​တွေကသူတို့ရဲ့ life cycle မှာမတူညီတဲ့ different states ​တွေကိုဖြတ်သန်းရပါတယ်။ ဒီ states ​တွေကိုမြင်သာ​အောင် ​အောက်ကပုံ​လေးနဲ့ တွဲကြည့်​ပေးပါ။ စာ​ရေးသူတို့ဟာ Linux system တစ်ခုကို စပြီး boot တက်လိုက်ပြီဆိုတာနဲ့ init process ဆိုတဲ့ process တစ်ခုကို machine ကစ run လိုက်ပါတယ်။ ယခု​နောက်ပိုင်း modern system ​တွေမှာ​တော့ init အစား systemd ကို​ပြောင်းလဲ အသုံးပြုလာတာ​ဖြစ်ပါတယ်။ ဒါ​ပေမယ့် သူတို့ ၂ခုလုံးရဲ့တူညီတာက​တော့ vmlinuz ဆိုတဲ့ Linux kernel executable ကို memory ​ပေါ်ဆွဲတင်လိုက်တာက​နေ Linux kernel က create လုပ်လိုက်တဲ့ mother process လို့​ပြောလို့ရတာပဲဖြစ်ပါတယ်။ အဲ့​တော့ ဒီ init process မှာ​တော့ parent process ရယ်လို့မရှိ​တော့ပါဘူး။ သူက​နေမှတစ်ဆင့် ဒီ system ထဲမှာရှိတဲ့ process ​တွေ​မွေးဖွားလာမှာဖြစ်ပါတယ်။  Linux boot process step by step ဘယ်လို အလုပ်လုပ်လဲဆိုတာကို​တော့ ​နောက်မှ post တစ်ခုနဲ့သပ်သပ် sharing ထပ်လုပ်ပါဦးမယ်။ ကဲ ပြန်ဆက်လိုက်ကြရ​အောင်.. အဲ့​တော့ ဒီ init process ​နေကမှကျွန်​တော်တို့ ဟိုတစ်​နေ့ကသိခဲ့တဲ့ fork() function ကိုအသုံးပြုပြီး child process ​တွေဆက်လက်​ပေါ်​ပေါက်လာတာဖြစ်ပါတယ်။ အဲ့​တော့စာ​ရေးသူတို့က ps command နဲ့ running process ​တွေကိုကြည့်ကြည့်မယ်ဆိုရင် စာ​ရေးသူတို့ run လိုက်တဲ့ commands ​တွေက (အ​ပေါ်က ps command အပါအဝင်) shell ရဲ့ child process အ​နေနဲ့ရှိ​နေတာ ​တွေ့မြင်ရမှာပါ။ ဒီလိုပဲ ကျွန်​တော်တို့မြင်ရတယ့် GUI ​တွေကလည်း အ​ပေါ်မှာ​ပြောခဲ့တဲ့ init process ရဲ့ child process ​တွေအ​နေနဲ့တည်ရှိ​နေတာပါ။ 
Process တစ်ခု စတင်ဖြစ်​ပေါ်လာတဲ့ အချိန်ကစလို့ သူ့ရဲ့ task ပြီးဆုံးသွားတဲ့အချိန်ထိ ဖြတ်​ကျော်ရတဲ့ အဆင့် ၄ဆင့်ကို တစ်ခုချင်းဆီ​ပြောသွားပါမယ်။

1. 𝑹𝒆𝒂𝒅𝒚 / 𝑹𝒖𝒏𝒏𝒊𝒏𝒈 

ဒီ state မှာ​တော့ process ​တွေဟာလက်ရှိ CPU ​ပေါ်မှာ processing time ယူ​နေပြီး execute လုပ်​နေတာဖြစ်နိုင်သလို run ဖို့ ready ဖြစ်​နေပြီး scheduler က assign ချမ​ပေး​သေးလို့ ​စောင့်​နေရတဲ့ process ​တွေလည်းဖြစ်နိုင်ပါတယ်။ 

2. 𝑾𝒂𝒊𝒕𝒊𝒏𝒈 / 𝑺𝒍𝒆𝒆𝒑𝒊𝒏𝒈 

ဒီ state မှာ​တော့ process တစ်ခုဟာ run ​နေရင်း event တစ်ခုခုကို​စောင့်​နေတာမျိုး၊ ဥပမာအားဖြင့် hard disk ​ပေါ်မှာရှိတဲ့ file တစ်ခုကိုဖတ်ဖို့လိုတယ်ဆိုရင် I/O wait time ရှိတဲ့အတွက်​​ကြောင့် run ​နေတဲ့ state က​နေ ဒီ process ဟာ sleeping state ကို​ပြောင်းခံလိုက်ရပါတယ်။ ​နောက်သူလိုအပ်တဲ့ I/O လုပ်ပြီးပြီဆိုရင်​တော့ ဒီ process ဟာတစ်ဖန်ပြန်ပြီး running လုပ်ဖို့အတွက် queue ထဲမှာ ready state အ​နေနဲ့ ပြန်​စောင့်ရမှာပဲ ဖြစ်ပါတယ်။ အဲ့​တော့မှ scheduler အ​နေနဲ့ ဒီ process ကို cpu run time ပြန်သတ်မှတ်​ပေးဖို့ လုပ်​ဆောင်မှာဖြစ်ပါတယ်။ 

3. 𝑻𝒆𝒓𝒎𝒊𝒏𝒂𝒕𝒆𝒅 / 𝑺𝒕𝒐𝒑𝒑𝒆𝒅 

ဒီ state က​တော့ Process တစ်ခုက သူ့ရဲ့ run ရတဲ့ ရည်ရွယ်ချက်ပြီး​​မြောက်သွားလို့ exit() function နဲ့ထွက်သွားတာ ဖြစ်နိုင်သလို၊ တစ်ခြား process က​​နေ signal တစ်ခုခုနဲ့ interupt လုပ်လို့ stopped ဖြစ်သွားတာလည်းဖြစ်နိုင်ပါတယ်။ ဒီ state မှာဆိုရင်​တော့ process table ထဲက​နေပါ ထွက်သွားမှာပဲ ဖြစ်ပါတယ်။ Signals ​တွေနဲ့ပတ်သက်ပြီး​တော့လည်း ​နောက်မှအ​သေးစိပ်​ရေးပါမယ်၊ ​လော​လောဆယ်​တော့ SIGTERM or SIGSTOP လိုမျိုး signals ​တွေဟာ process ​တွေကို Stopped ချင်ရင် အသုံးပြုလို့ရတယ်​လောက်သာ သိထားရင်ရပါပြီ။ 

4. 𝒁𝒐𝒎𝒃𝒊𝒆 𝑺𝒕𝒂𝒕𝒆 

Zombie state ဆိုတာက​တော့ process တစ်ခုဟာ stopped ဖြစ်ပြီး​နောက်ပိုင်း သူ့ရဲ့ parent process က exit status ကို collect လုပ်ပြီး process table က​နေ မဖယ်ရှား​ပေးခင်မှာ ဒီ child process ဟာ zombie state မှာရှိ​နေမှာပဲဖြစ်ပါတယ်။ 

𝐈𝐧𝐭𝐞𝐫-𝐩𝐫𝐨𝐜𝐞𝐬𝐬 𝐜𝐨𝐦𝐦𝐮𝐧𝐢𝐜𝐚𝐭𝐢𝐨𝐧

ဒီအပိုင်းမှာ​တော့ စာ​ရေးသူတို့ system ထဲမှာရှိတဲ့ process ​တွေဟာ အချင်းချင်း communicate ဘယ်လိုလုပ်ကြလဲ၊ ပြီး​တော့ parent process ​တွေက​ကော သူ့ရဲ့ သက်ဆိုင်တဲ့ child process ​တွေကိုဘယ်လို manage လုပ်လဲဆိုတာ​တွေနဲ့ပတ်သက်တာကို​ပြောသွားပါမယ်။ ကျွန်​တော်တို့ inter-process communication လုပ်တဲ့​နေရာမှာ oldest way က​တော့ signal ပို့တဲ့နည်းလမ်းပဲဖြစ်ပါတယ်။ ကျွန်​တော်တို့ အ​ပေါ်မှာ ​ပြောခဲ့တဲ့ signals ​တွေကို user က​နေ kill or pkill command နဲ့ဖြစ်​စေ process ​တွေအချင်းချင်း ကဖြစ်​စေပို့နိုင်ပါတယ်။ ဒီ signals ​တွေကိုလက်ခံရရှိတဲ့အချိန်မှာ ဒီ process or running program ​တွေကသူတို့ဒီ signal ကို ဘာလုပ်ရမလဲဆိုတဲ့ Default action ကိုပြုလုပ်သွားပါတယ်။ ဒါမှမဟုတ်ကျွန်​တော်တို့က ဒီ signal ကိုရရင် ဘာလုပ်ပါဆိုတဲ့ handler ထည့်ထားလို့လည်းရပါတယ်။ ဒါမှမဟုတ် ဒီ signal လာလည်းဘာမှမလုပ်ဘူးဆိုပြီး ignore လုပ်ထားလို့လည်းရပါတယ်။ ဒါ​ပေမယ့်အဲ့လို ignore လုပ်ထားလို့မရတဲ့ signals ​တွေလည်းရှိပါတယ်။ ဥပမာအားဖြင့် SIGSTOP နဲ့ SIGKILL ကိုဆိုရင် ignore လုပ်လို့မရပါဘူး၊ SIGKILL ပို့ခံရတဲ့ process တစ်ခုဟာ force kill လုပ်ခံကိုခံရပါမယ်၊ အဲ့လို​ပြောချင်တာပါ။ 
တစ်ခြား Inter-Process Communication မှာသုံးတဲ့ နည်းလမ်း ၂ခုအ​ကြောင်းဆက်​ပြောသွားပါမယ်။

1. 𝑺𝒉𝒂𝒓𝒆𝒅 𝒎𝒆𝒎𝒐𝒓𝒚

ပထမ နည်းလမ်းတစ်ခုက​တော့ different process ၂ခုက သူတို့အချင်းချင်း communicate လုပ်ပြီး process တစ်ခုရဲ့ action ​တွေ၊ information ​တွေကိုတစ်ခြား process ကသိ​အောင် memory segment ကို စုသုံးတဲ့ ပုံစံနဲ့
ပြုလုပ်လို့ရပါတယ်။ သ​ဘောက​တော့ process A နဲ့ process Bလို့ပဲထားပါ​တော့၊ process A ကသူလုပ်ခဲ့တဲ့ information ​တွေ၊ သူသုံးခဲ့တဲ့ computation ​တွေကို memory segment တစ်ခုထဲမှာ buffer အ​နေနဲ့သိမ်းခဲ့ပါတယ်၊ process B က ဒီ information ​တွေကိုအသုံးပြုပြီး task တစ်ခုခုပြုလုပ်ဖို့လိုအပ်လာတဲ့အခါ ဒီ shared လုပ်ထားတဲ့ memory segment ထဲကသွားယူပြီးသုံးတဲ့ပုံစံကို​ပြောတာပါ။

2. 𝑴𝒆𝒔𝒔𝒂𝒈𝒆 𝑷𝒂𝒔𝒔𝒊𝒏𝒈 

ဒုတိယနည်းလမ်းက​တော့ process အချင်းချင်းကြားမှာ ​ပေးပို့ချင်တဲ့ specific information ​တွေကို message တစ်ခုအ​နေနဲ့ header, body ခွဲပြီး communication link တစ်ခုက​နေ အပြန်အလှန် ဆက်သွယ်တဲ့ပုံစံပါ။ Communication link ​နေရာမှာ direct communication နဲ့ indirect communication လို့ ၂မျိုးထက်ကွဲပြီး direct communication ဆိုတာက​တော့ sender က message ပို့တဲ့အချိန်မှာ ဘယ် receiver ဆီကိုပို့မယ်ဆိုတာကို ပုံ​သေသတ်မှတ်​ပေးလိုက်တာကို​ပြောချင်တာပါ။ Indirect communication မှာ​တော့ process ​တွေဟာ အချင်းချင်း message share နိုင်ဖို့အတွက် mailbox တစ်ခုကို share သုံးရတယ့်ပုံကို​ပြောချင်တာပါ။ mailbox ဆိုတာကို port တစ်ခုအ​နေနဲ့မြင်ကြည့်နိုင်ပါတယ်။ ဒီ​နေရာမှာ​တော့ one to one communication မဟုတ်ပဲ multiple senders က​နေ receiver တစ်​ယောက်ဆီကို message ​ပေးပို့တာလည်းဖြစ်နိုင်ပါတယ်။ ဒီ share လုပ်ထားတဲ့ mailbox ကို​တော့ receiver process ဘက်က create လုပ်တာဖြစ်ပြီး receiver process terminate လုပ်သွားချိန်မှာ တစ်ခါထဲ destroy လုပ်ခဲ့လို့ရပါတယ်။ 
ကဲ​ပြောတာ​တွေလည်းများသွားပြီထင်ပါတယ်၊ ဒီ​နေ့မှာ​တော့ ဒီ​လောက်နဲ့ပဲရပ်ပြီး ​နောက်တစ်​နေ့မှာ​​တော့ ကျွန်​တော်တို့ CPU context switching ဆိုတဲ့​ခေါင်းစဥ်နဲ့ စပြီး 1 core ပဲပါတဲ့ CPU တစ်ခုက multiple processes ​တွေကိုဘယ်လို handle လုပ်လဲဆိုတာ ထပ်မံ​ပြောသွားပါမယ်။ 

အားလုံးကို​ကျေးဇူးတင်ပါတယ်။ 
