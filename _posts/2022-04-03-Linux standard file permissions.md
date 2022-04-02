---
layout: post
title: Linux standard file permissions
subtitle: How to manipulate file permissions
thumbnail-img: /assets/img/file permissions.png
tags: [Linux]
---
အားလုံးပဲ မင်္ဂလာပါ။ Heinux blog မှ ကြိုဆိုလိုက်ပါတယ်။ 

ဒီ​နေ့မှာ​တော့ ကျွန်​တော်က Linux မှာ file permissions ​တွေနဲ့ပတ်သက်ပြီး ဘယ်လိုသတ်မှတ်ချက်​တွေရှိလဲ၊ ကိုယ့်ရဲ့လိုအပ်ချက်အရ အဲ့ permissions ​တွေကို ဘယ်လို manipulate လုပ်ရမလဲဆိုတာကို ​ပြောသွားပါမယ်။ 

ကျွန်​တော်တို့ရဲ့ system ထဲက directory တစ်ခုခုမှာရှိတဲ့ files ​တွေကို listing လုပ်ကြည့်ချင်ရင် ls command ကိုသုံးတယ်လို့ ကျွန်​တော်တို့သိထားပါတယ်။ အဲ့​တော့ ဒီ files ​တွေနဲ့ directories ​တွေရဲ့ permissions ​တွေကိုပါကြည့်ချင်တယ်ဆို ဒီ ls -l ဆိုတဲ့ command ​လေးနဲ့ကြည့်ကြည့်ရ​အောင်။ 

>ls -l /home/hhw

![home-files-ss](/assets/img/homefiles.JPG) 

ဒီပုံမှာမြင်ရမှာက​တော့ ကျွန်​တော်ရဲ့ ubuntu-test ဆိုတဲ့ machine ထဲက /home/hhw ဆိုတဲ့ directory ​အောက်မှာရှိတဲ့ files ​တွေနဲ့ sub directories ​တွေရဲ့ permissions ​တွေပဲဖြစ်ပါတယ်။ Directories ​တွေကို ခွဲခြားသိဖို့ command ရဲ့ output မှာထိပ်ဆုံး ကိုကြည့်ရင် d ဆိုတာ directory ကိုရည်ညွှန်းပါတယ်။ ရိုးရိုး file ဆိုရင် - symbol ​လေးနဲ့ပြမှာဖြစ်ပြီး symbolic link ဆိုရင်​တော့ l ဆိုတဲ့ symbol ​လေးရှိ​နေမှာပါ။ အဲ့​နောက်မှာဆက်​တွေ့ရမယ့် rwx ဆိုတာ​တွေက​တော့ ဒီ files or directories ရဲ့ permissions ​တွေပဲ ဖြစ်ပါတယ်။ ​အောက်မှာအ​သေးစိပ်ဆက်​ပြောပါမယ်။ 

ဟုတ်ပြီ ကျွန်​တော်တို့ ဒီ /home/hhw directory ထဲမှာရှိတဲ့ files ​တွေနဲ့ sub directories ​တွေရဲ့ attributes ​တွေ၊ permissions ​တွေကို​တော့ကြည့်ပြီးပြီ၊ ဒီ parent directory ကြီးကိုယ်တိုင်ရဲ့ permission ​တွေ၊ owner ​တွေကိုကြည့်ချင်တယ်ဆိုရင်​ရော 

>ls -ld /home/hhw

ဆိုပြီးကြည့်လို့ရပါတယ်။ ​အောက်ပါအတိုင်းမြင်ရမှာပါ။

![homedir](/assets/img/homedir.PNG)
 
ဒီ file permissions ​တွေကိုကြည့်တဲ့အခါမှာ ကျွန်​​တော်တို့ သုံးပိုင်းခွဲကြည့်ပါမယ်။ ပထမဆုံး rwx ဆိုတဲ့ အပိုင်းက​တော့ ဒီ file ရဲ့ owner (user) ရဲ့ permissions ကိုကိုယ်စားပြုပါတယ်။ ဒုတိယ rwx ဆိုတဲ့အပိုင်းက​တော့ ဒီ file ရဲ့ group owners ( group ) ရဲ့ permissions ​ကိုကိုယ်စားပြုပါတယ်။ တတိယ အပိုင်းက r-x လို့​တွေ့​နေရတဲ့ အပိုင်းက​တော့ ဒီ system ထဲမှာရှိ​နေတဲ့ တစ်ခြား users ​တွေအကုန် ( others ) ရဲ့ permission ကိုကိုယ်စားပြုပါတယ်။ 

![permissions](/assets/img/1.png)

**chmod**

ဒီ permissions ​တွေကို change ချင်တယ်ဆိုရင်​တော့ chmod command ကိုသုံးပြီး change နိုင်မှာ ဖြစ်ပါတယ်။ အဲ့မှာမှ ကျွန်​တော်တို့ ပုံစံ ၂မျိုးနဲ့ change လို့ရပါတယ်။ ကျွန်​တော်တို့ u+rwx, g+rwx ဆိုပြီး symbolic ပုံစံမျိုးနဲ့ change လို့လည်းရပြီး chmod 770 ဆိုပြီး numeric code ​ပုံစံမျိုး အသုံးပြုပြီး​တော့လည်း change လို့ရပါတယ်။ ​အောက်မှာ symbol ​တွေရဲ့ ဆိုလိုရင်းနဲ့ သူတို့နဲ့ တူညီတဲ့ numeric value ​တွေကို ​ဖော်ပြ​ပေးသွားပါမယ်။ 

![octal-values](/assets/img/2.png)

ဘယ်​နေရာမှာ ဘယ်လို format နဲ့သုံးမလဲ ဆိုတာက​တော့ ကိုယ်သင့်​တော်သလို ​ရွေးချယ်ပြီးသုံးရမှာပါ။ 

ဥပမာ အ​​နေနဲ့ ကျွန်​တော်တို့က ရှိပြီးသား file တစ်ခုကို group နဲ့ other users ကို read and execute permission ​ထပ်ပေးချင်တယ်ဆိုပါ​တော့၊ ဒါဆိုရင် 

>chmod go+rx (file-name) 

ဆိုပြီးသုံးလို့ရပါတယ်။ 

ထိုနည်းတူစွာပဲ ကျွန်​တော်တို့က ရှိပြီးသား permission တစ်ခုခုကို ပြန်ရုတ်သိမ်းချင်တယ်ထားပါ​တော့၊ other users ကို execute permission မ​ပေးချင်ဘူးဆိုရင် ဒီလိုသုံးလို့ရပါတယ်။ 

>chmod o-x (file-name) 

ဒါ​ပေမဲ့ file တစ်ခုကို အသစ် create ပြီးကျွန်​​တော်တို့က file owner နဲ့ group owners ​တွေကို​တော့ permissions အပြည့်​ပေးချင်တယ်၊ others ကို​တော့ ဘာ permissions မှ မ​ပေးချင်ဘူး၊ အဲ့လို တိတိကျကျ သိ​နေတာမျိုးဆို 

>chmod 770 (file-name) 
ဆိုပြီးအလွယ်တစ်ကူသုံးနိုင်ပါတယ်။ 

>chmod u=rwx,g=rwx,o= (file-name) 
ဆိုတဲ့ command နဲ့ သ​ဘောတရား အတူတူပါပဲ။ 

​နောက်ဥပမာတစ်ခုအ​နေနဲ့ ကျွန်​တော်တို့က script file တစ်ခု create ပြီးပြီ ထားပါ​တော့၊ အဲ့ file ကို shell က​နေ execute လုပ်နိုင်​အောင် execute permission ထည့်ချင်တယ်ဆိုရင် 

>chmod a+x myscript.sh 

ဆိုပြီးထည့်လိုက်လို့ရပါတယ်။ a ဆိုတာ all ကိုကိုယ်စားပြုပြီး **ugo+x** လို့သုံးတာနဲ့ သ​ဘောတရားတူပါတယ်။ 

**Changing file ownership**

ကျွန်​တော်တို့က file တစ်ခုရဲ့ owner နဲ့ group owner ကို​ပြောင်းချင်တဲ့ အချိန်မှာ chown ဆိုတဲ့ command ကိုအသုံးပြုနိုင်ပါတယ်။ ဒါ​ပေမဲ့ အဲ့လို​ပြောင်းဖို့အတွက် ကိုယ်က ဒီ file ရဲ့ owner သို့မဟုတ် super user access ရှိဖို့​တော့လိုအပ်ပါတယ်။ ဥပမာအ​နေနဲ့ ကျွန်​တော့်စက်ထဲက hhw ပိုင်တဲ့ file တစ်ခုကို တစ်ခြား user တစ်​ယောက်အပိုင်ဖြစ်​အောင် ​ပြောင်းကြည့်ပါမယ်။ 

>ls -l testfile1

![before](/assets/img/before.PNG)


>sudo chown anna testfile1 

![after](/assets/img/after.PNG)

ဒီ​နေ့မှာ​တော့ Linux file standard permissions ​တွေအ​ကြောင်း​ပြောခဲ့တာဖြစ်ပြီး knowledge ရမယ်လို့ ​မျှော်လင့်ပါတယ်။ ​နောက်တစ်​နေ့မှာ​တော့ ဒီ user, group, others လို့အုပ်စုသုံးခုခွဲပြီး သက်ဆိုင်ရာ permissions ​တွေသတ်မှတ်​ပေးထားတာထက်ပိုပြီး ဘယ်လို advanced permissions ​တွေရှိ​သေးလည်း ဆိုတာကိုဆက်​ရေးသွားပါမယ်။ 

အားလုံးပဲ​ကျေးဇူးတင်ပါတယ်။ 

𝓗𝓮𝓲𝓷𝓾𝔁 𝓫𝓵𝓸𝓰
