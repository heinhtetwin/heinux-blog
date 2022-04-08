---
layout: post
title: Advanced file permissions in Linux
thumbnail-img: /assets/img/Advanced file permissions in Linux.png
share-img: /assets/img/Advanced file permissions in Linux.png
tags: [Linux]
---

𝐀𝐝𝐯𝐚𝐧𝐜𝐞𝐝 𝐟𝐢𝐥𝐞 𝐩𝐞𝐫𝐦𝐢𝐬𝐬𝐢𝐨𝐧𝐬 𝐢𝐧 𝐋𝐢𝐧𝐮𝐱  

ဟိုတစ်​နေ့က​တော့ ကျွန်​တော်တို့ Linux မှာရှိတဲ့ standard file permissions ​တွေအ​ကြောင်း​ပြောခဲ့ပါတယ်။ ဒီတစ်​ခေါက်မှာ​တော့ Linux မှာရှိတဲ့ advanced file permissions ​တွေအ​ကြောင်း sharing လုပ်သွားပါမယ်။ 

✅𝐒𝐞𝐭 𝐔𝐈𝐃

ဒီ section မှာ set uid ဆိုတာဘာလဲ၊ ဘယ်လို permission ​ပေးရမလဲဆိုတာကို မ​ပြောခင် ကျွန်​တော်​ရေးသွားမယ့်ပုံစံကို အရင်​ပြောပါမယ်။ ဒီ special permission ​တွေကို သာမန် files ​တွေမှာ ​ပေးတာနဲ့ directory ​ပေါ်မှာ ​ပေးတာနဲ့ဘာကွာလဲ ဆိုတာကို ၂ပိုင်းခွဲပြီး ​ရေးသွားပါမယ်။ 

✅𝐒𝐔𝐈𝐃 𝐨𝐧 𝐧𝐨𝐫𝐦𝐚𝐥 𝐟𝐢𝐥𝐞𝐬

ဒီ set uid bit ကို ရိုးရိုး normal files ​တွေမှာ ဘယ်လိုထည့်ရမလဲဆို​တော့ 𝐜𝐡𝐦𝐨𝐝 𝐮+𝐬 ဆိုပြီး​နောက်မှာ ကိုယ်ထည့်ချင်တဲ့ file ရဲ့ path ကိုထည့်​ပေးရပါမယ်။ သူကဘာလုပ်​ပေးတာလဲဆို​တော့ သာမန် ကျွန်​တော်တို့ user တစ်​ယောက်က file တစ်ခုကို read ပြီထားပါ​တော့၊ ဒါဆို Linux ကစစ်ပါလိမ့်မယ်၊ ဒီ user က file ရဲ့ owner လား၊ ဒါမှမဟုတ် group owner ထဲမှာပါလား၊ ဒါမှမဟုတ် others user လားဆိုပြီး စစ်ပါလိမ့မယ်။ ပြီး​တော့မှ ထားပါစို့ ဒီ run ချင်တဲ့ user က owner လည်းမဟုတ်ဘူး၊ group owner ထဲလည်းမပါဘူး၊ ဒါဆို ဒီ​ကောင်က others ထဲမှာအကြုံးဝင်တယ်၊ အဲ့​တော့ others ကို ဘာ permissions ​တွေ​ပေးထားလည်းကြည့်မယ်၊ အကယ်၍ read permission ပါတယ်ဆိုရင်​တော့ ဖတ်လို့ရမယ် user ကဒီသူဖတ်ချင်တဲ့ file ကို၊ ဒါ​ပေမဲ့ ဒီ particular user ရဲ့ privilege နဲ့ပဲ ဒီ file ကို run လို့ရမယ်။ ဒီလိုပုံစံမျိုးသွားပါတယ်။ 
ဒါ​ပေမဲ့ ခုဏက​ပြောခဲ့တဲ့ file ​ပေါ်မှာပဲ set uid bit သတ်မှတ်​ပေးထားတယ်ဆိုပါစို့၊ ဒါဆိုရင်​တော့ ဒီ owner လည်းမဟုတ်၊ group owner လည်းမဟုတ်တဲ့ user ဟာဒီ file ကို သူ့ရဲ့ permissions နဲ့ပဲမဟုတ်ပဲ ဒီ file ကိုတစ်ကယ်ပိုင်တဲ့ owner ရဲ့ privileges နဲ့ run လို့ရသွားမှာပါ။ အဲ့​တော့​ပြောချင်တာက ဒီ script file လိုမျိုးတစ်ခုကို root ကပိုင်တယ်ဆို အဲ့​ပေါ်မှာ suid bit ရှိ​နေမယ်ဆို privilege escalation လိုမျိုး security vulnerability ​တွေမျိုးဖြစ်နိုင်ပါတယ်။ ဒါ့​ကြောင့်ဘယ် files ​ပေါ်မှာ ဒီ SUID permission ​ပေးမလဲဆိုတာကို ​သေချာစဥ်းစားရပါမယ်။ default အ​နေနဲ့​တော့ sudo command တို့ passwd command တို့ရဲ့ binary file ​တွေမှာ set uid bit ပါပါတယ်။ အဲ့တာမှ ကျွန်​တော်တို့က သာမန် user က​နေ sudo ရိုက်ပြီး root အ​နေနဲ့ command ​တွေ run နိုင်​အောင်ပါ။ ဒီ SUID ကို octal အ​နေနဲ့လည်းထည့်လို့ရပါ​သေးတယ်။ 

𝐄.𝐠. 𝐜𝐡𝐦𝐨𝐝 𝟒𝟕𝟓𝟓 <𝐟𝐢𝐥𝐞-𝐧𝐚𝐦𝐞> 
ဆိုတဲ့ပုံမျိုးနဲ့ထည့်လို့ရပါတယ်။ ​ရှေ့ဆုံးက 4 က SUID ကိုကိုယ်စားပြုပါတယ်။ 

✅𝐒𝐔𝐈𝐃 𝐨𝐧 𝐝𝐢𝐫𝐞𝐜𝐭𝐨𝐫𝐢𝐞𝐬 

Set UID ကို directory ​ပေါ်မှာ​ပေးတာက​တော့ ဘာ effects မှမရှိပါဘူး။ shell က neglect လုပ်သွားမှာပါ။ 

✅𝐒𝐆𝐈𝐃 𝐨𝐧 𝐧𝐨𝐫𝐦𝐚𝐥 𝐟𝐢𝐥𝐞𝐬 

ဟုတ်ပြီ၊ ကျွန်​တော်တို့ SUID အ​ကြောင်း​​ပြောပြီးပြီ ဆို​တော့ SGID အ​ကြောင်းဆက်ကြည့်လိုက်ရ​အောင်။ Set GID bit ကို normal files ​တွေ​ပေါ်မှာ permission ​ပေးထားမယ်ဆိုရင် ဘာလုပ်​ပေးလဲဆို​တော့ သူကလည်း SUID လိုပါပဲ၊ ဒီ file ကိုလာ run တဲ့ user ရဲ့ permissions နဲ့မဟုတ်ပဲ ဒီ file ကိုပိုင်တဲ့ group owner ​တွေရဲ့ permissions နဲ့ run ​ပေးမှာပါ။
ဒီ SGID bit ကိုဘယ်လိုထည့်မလဲ ဆိုတာကြည့်ရ​အောင်၊ နည်း ၂မျိုးနဲ့ထည့်လို့ရပါတယ်။ 

𝐄.𝐠.𝟏. 𝐜𝐡𝐦𝐨𝐝 𝐠+𝐬 <𝐩𝐚𝐭𝐡-𝐭𝐨-𝐲𝐨𝐮𝐫-𝐟𝐢𝐥𝐞> 

𝐄.𝐠.𝟐. 𝐜𝐡𝐦𝐨𝐝 𝟐𝟕𝟓𝟓 <𝐩𝐚𝐭𝐡-𝐭𝐨-𝐲𝐨𝐮𝐫-𝐟𝐢𝐥𝐞>
ပထမဆုံး 2 ဆိုတဲ့ octal representation က SGID bit ကိုကိုယ်စားပြုပါတယ်။ SUID ​ကော SGID ​ကော file တစ်ခုထဲမှာထည့်ချင်ရင်လည်း ဒီလိုသုံးလို့ရပါတယ်။ 

𝐄.𝐠. 𝐜𝐡𝐦𝐨𝐝 𝟔𝟕𝟓𝟓 <𝐩𝐚𝐭𝐡-𝐭𝐨-𝐲𝐨𝐮𝐫-𝐟𝐢𝐥𝐞> 
SUID ရဲ့ 4 နဲ့ SGID 2 values ၂ခု​ပေါင်းပြီး​ရှေ့ဆုံး bit မှာ 6 ဖြစ်သွားတာပါ။ read, write, execute ​ပေါင်းလိုက်ရင် 7 ဖြစ်တာနဲ့ သ​ဘောတရား တူတူပါပဲ။ 

✅𝐒𝐆𝐈𝐃 𝐨𝐧 𝐝𝐢𝐫𝐞𝐜𝐭𝐨𝐫𝐢𝐞𝐬  
ဒီ SGID permission ကို directory တစ်ခု​ပေါ်မှာ ​ပေးမယ်ဆိုရင်​ရော ဘာ​တွေ​ပြောင်းလဲသွားမလဲ ကြည့်ရ​အောင်။ ပုံမှန်ဆိုရင် ကျွန်​တော်တို့က file အသစ်တစ်ခု ဒါမှမဟုတ် directory တစ်ခု create ပြီထားပါ​တော့၊ ကျွန်​တော်တို့ chown or chgrp command သုံးပြီး group owner မ​ပြောင်းထားဘူးဆိုရင် ဒီ files ​တွေရဲ့ group owner က user owner ရဲ့ primary group ပဲ ဖြစ်​နေမှာပါ။ ဒါ​ပေမဲ့ SGID bit ကို Directory ​ပေါ်မှာ set ထားတယ်ဆိုရင်​တော့ အဲ့ directory ​အောက်မှာ အသစ်ထပ် create မဲ့ sub directories ​တွေ၊ normal files ​တွေရဲ့ group owner က ဒီ parent directory မှာရှိတဲ့ group owner ဆီက​နေ inherit လုပ်သွားမှာပဲ ဖြစ်ပါတယ်။ ဆိုလိုတာသည် ဒီ files ​တွေကိုထပ် create လုပ်တဲ့ user owner ရဲ့ group မဟုတ်​တော့ဘဲ ဒီ parent directory ရဲ့ group owner ပဲဖြစ်သွားမှာပါ။ 

𝐄.𝐠. 𝐜𝐡𝐦𝐨𝐝 𝐠+𝐬 <𝐩𝐚𝐭𝐡-𝐭𝐨-𝐲𝐨𝐮𝐫-𝐝𝐢𝐫>  

✅𝐒𝐭𝐢𝐜𝐤𝐲 𝐛𝐢𝐭 𝐨𝐧 𝐟𝐢𝐥𝐞𝐬 

Sticky bits permission ကို normal files ​တွေ​ပေါ်မှာ ထားမယ်ဆိုရင်​တော့ ဘာ effects မှရှိမှာမဟုတ်ပါဘူး။ shell က execute လုပ်တဲ့အချိန်မှာ neglect လုပ်သွားမှာပါ။ 

✅𝐒𝐭𝐢𝐜𝐤𝐲 𝐛𝐢𝐭𝐬 𝐨𝐧 𝐝𝐢𝐫𝐞𝐜𝐭𝐨𝐫𝐢𝐞𝐬

ဒီ sticky bit permission ကို directory level မှာ ထားမယ်ဆို ဘာ effects ​တွေရှိမလဲ ကြည့်ကြည့်ရ​အောင်။ ပုံမှန်ကျွန်​တော်တို့ directory တစ်ခုရှိတယ်ဆိုပါစို့။ ဒီ directory ရဲ့ group owner ထဲက users ​တွေဟာ ဒီ directory ​ပေါ်မှာ files ​တွေကို read and write လုပ်နိုင်တယ်ထားပါ​တော့၊ အဲ့မှာ user တစ်​ယောက်က create လုပ်သွားတဲ့ file ကို အဲ့ group ထဲမှာရှိတဲ့ တစ်ခြား user တစ်​ယောက်က write permission မရှိရင်​တောင် delete လုပ်လိုက်လို့ရပါတယ်။ sticky bits permission ရှိ​နေတယ်ဆိုရင်​တော့ အဲ့လိုမရ​တော့ပါဘူး၊ directory ထဲမှာ user တစ်​ယောက် create လုပ်ထားတဲ့ file ကို delete လုပ်ချင်တယ်ဆိုရင် အဲ့ file ရဲ့ owner user ကပဲ delete လုပ်လို့ရပါ​တော့မယ်။ ဒါ​ပေမဲ့လည်း ချွင်းချက်​တော့ရှိပါတယ်။ ဘာလဲဆို​တော့ root user ဒါမှမဟုတ် အဲ့ parent directory ရဲ့ owner user က​တော့ ဒီ directory ထဲမှာရှိတဲ့ files ​တွေအကုန်လုံးကို delete လုပ်ချင်ရင် လုပ်လို့ရပါတယ်။ 
sticky bit ကိုဘယ်လို ထည့်မလဲဆိုတာ ကြည့်လိုက်ရ​အောင်... 

𝐄.𝐠. 𝐜𝐡𝐦𝐨𝐝 +𝐭 <𝐩𝐚𝐭𝐡-𝐭𝐨-𝐲𝐨𝐮𝐫-𝐝𝐢𝐫>
ဆိုတဲ့ပုံစံမျိုးနဲ့ထည့်လို့ရပါတယ်။ အ​ပေါ်မှာလိုပဲ octal representation နဲ့ထည့်ချင်လည်းရပါတယ်။ sticky bit ရဲ့ equivalent က 1 ပါ။ 

𝐄.𝐠. 𝐜𝐡𝐦𝐨𝐝 𝟏𝟕𝟕𝟓 <𝐩𝐚𝐭𝐡-𝐭𝐨-𝐲𝐨𝐮𝐫-𝐝𝐢𝐫> ဆိုပြီးလည်းသုံးလို့ရပါတယ်။ 

Linux မှာရှိတဲ့ Advanced file permissions ​တွေက​တော့ ဒါ​တွေပါပဲ။ 
ဖတ်​ပေးတဲ့သူအားလုံးကို ​ကျေးဇူးတင်ပါတယ်။ 

𝓗𝓮𝓲𝓷𝓾𝔁 𝓫𝓵𝓸𝓰
