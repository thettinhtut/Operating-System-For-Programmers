## Scheduling

![Image of Abstraction](https://raw.githubusercontent.com/HlaingTinHtun/Operating-System-For-Programmers/master/images/scheduling.png)

ပုံမှန် process manager တွေကလုပ်နေတဲ့ activity တွေဖြစ်တဲ့ process ကို remove လုပ်တာတို့  process တစ်ခုပြီးသွားရင် နောက်တစ်ခုကို select လုပ်ပြီး run တာတို့ကို process scheduling လို့ခေါ်ပါတယ်။ process scheduling က OS တစ်ခုမှာ multi processing ကိုလုပ်ပေးနိုင်ဖို့အတွက်အရေးကြီးတဲ့ အစိတ်အပိုင်းတစ်ခုဖြစ်ပါတယ်။ ဘာလို့လဲဆိုတာကို ဆက်ဖတ်ကြည့်လိုက်ရအောင်။

အရင် process article မှာတုန်းက PCB Block အကြောင်းတွေပြောထားပါတယ်၊ အဲ့ဒီ PCB တွေအားလုံးက OS က Process scheduling queue ထဲမှာသိမ်းထားပါတယ်။ ဘယ်လိုသိမ်းထားလည်းဆိုတော့ process တွေရဲ့ state ပေါ်မူတည်ပြီးသိမ်းပါတယ်၊ ဥပမာ waiting ဖြစ်နေတဲ့ process တွေဆို waiting queue, ready ဖြစ်နေတဲ့ process တွေဆို ready queue စသည်ဖြင့်အဲ့လို ခွဲပြီး သိမ်းထားပါတယ်။ process တစ်ခုရဲ့ state ပြောင်းသွားပြီဆိုတာနဲ့ အဲ့ဒီ process ရဲ့ PCB ဟာလက်ရှိ ရှိနေတဲ့ queue ကနေ သူရဲ့ state နဲ့ သက်ဆိုင်တဲ့ queue ထဲကို move လုပ်သွားပါတယ်၊ ဥပမာ ထပ်ပေးရရင် ready ဖြစ်နေတဲ့  process ရဲ့ PCB က ready ဆိုတဲ့ queue ထဲမှာရှိမယ်၊ process ရဲ့ state က ready ကနေ running ဖြစ်သွားပြီဆို သူ့ရဲ့ PCB က ready queue ကနေ unlink လုပ်ပြီးတော့ running queue ဆီသွားသိမ်းပါတယ်၊ ဒီလိုသဘောတရားမျိုးဖြစ်ပါတယ်။

Queue တွေကို manage လုပ်ဖို့အတွက်ကို OS တွေကသုံးတဲ့ data structure တွေကလည်း ကွဲပြားပါတယ်။ ဥပမာ (FIFO, Round Robin, Priority Queue အစရှိသည်ဖြင့်) အသုံးပြုပြီးတော့ queue တွေကို manage လုပ်ပါတယ်။ Scheduling လုပ်တဲ့နေရာမှာ အဓိက process model ၂ ခုရှိပါတယ်။ Running & Not Running  ဖြစ်ပါတယ်။ Running model ကတော့ ရှင်းတယ်၊ process တစ်ခုစလိုက်ပြီရှိတာနဲ့ running model အဖြစ်သတ်မှတ်လို့ရပါတယ်။ Not Running model မှာတော့ running လုပ်ဖို့စောင့်နေတဲ့ queue တွေရှိမယ်၊ အဲ့ဒီ queue တွေကိုတော့ linked list ကိုသုံးပြီး create လုပ်ထားတယ် linked list အကြောင်း ကျနော်ရေးထားတာကို ဒီမှာ သွားဖတ်ကြည့်လို့ရပါတယ်။
http://bit.ly/33LGBsA
process တစ်ခုကို run နေရာကနေ interrupt လုပ်ခံရတာပဲဖြစ်ဖြစ်၊ အခုမှစပြီး run မလို့ပဲဖြစ်ဖြစ် waiting queue ထဲမှာရှိနေပါတယ်။ ပြီးသွားတဲ့ process တွေကိုတော့ discard လုပ်တယ်၊ ပြီးတာနဲ့ waiting queue ထဲက process တွေကို execute လုပ်ပါတယ်။

scheduler တွေရဲ့ အလုပ်ကို summarise ပြန်လုပ်ရရင် သူတို့ရဲ့ အဓိက အလုပ်က Job တွေကို select လုပ်ပြီး system ထဲမှာ execute လုပ်တာတို့ ဘယ် process ကို run မယ်ဆိုပြီး ဆုံးဖြတ်တာတို့ကိုလုပ်ပါတယ်။ ဒါပေမဲ့လည်း scheduler တွေကို system needs အရ သုံးမျိုးထပ်ခွဲထားပါသေးတယ်။ စာအရမ်းရှည်သွားမှာဆိုးတဲ့အတွက် ကျနော် ယေဘုယျပဲပြောသွားပါမယ်။
1.	Long Term Scheduler
ဒီကောင်ကိုတော့ Job scheduler လို့ခေါ်တယ်၊ ဘယ် programs တွေက process ဖြစ်လာဖို့စပြီး request လုပ်နေပြီလဲဆိုတာကို dertermine လုပ်ပေးပြီးတော့ queue ထဲက process တွေကို execute လုပ်ဖို့အတွက် memory ပေါ်တင်ပေးပါတယ်။
2.	Short Term Scheduler
CPU scheduler လို့ခေါ်သလို dispatcher လို့လဲခေါ်ပါတယ်။ ဘာလို့လဲဆိုတော့ ခုနက ပြောတဲ့ execute လုပ်ဖို့ memory ပေါ်ရောက်လာတဲ့ ကောင်တွေကို ready state ကနေ running state ကိုပြောင်းပြီး execute လုပ်ဖို့ CPU ထဲမှာ allocate လုပ်ပေးပါတယ်။
3.	Medium Term Scheduler (Swapping)
memory ပေါ်ကနေ process တွေကို remove လုပ်ဖို့အတွက်သုံးပါတယ်။ ဒါပေမဲ့ suspended ဖြစ်နေတဲ့ process (eg. IO requests တွေ )တွေလာရင်တော့ တန်းပြီး remove လုပ်လို့မရသေးပါဘူး။ memory ထဲမှာ နောက် process တွေအတွက်နေရာပေးပြီး suspend ဖြစ်နေတဲ့အတွက် ကောင်အတွက် secondary storage တစ်ခုထဲကို move လုပ်ပေးထားပါတယ်။ အဲ့ဒါကို swapping လုပ်တယ်လို့ခေါ်ပါတယ်။

context switch ဆိုတဲ့ အရာအကြောင်းလေးပြောပြီး နိဂုံးချုပ်ပါမယ်။ scheduling အကြောင်းပြောပြီဆိုရင်တော့ context switch အကြောင်းတော့ မပါလို့မရပါဘူး။ multitasking လုပ်နိုင်ဖို့အတွက် context switch ကအရေးပါတဲ့အရာတစ်ခုဖြစ်ပါတယ်။ ဘာလုပ်ပေးလဲဆိုတော့ process တစ်ခုက state change ရတော့မယ်ဆို အဲ့ process ရဲ့ context ကိုမှတ်ပေးထားပြီးတော့ လိုအပ်တဲ့အချိန်အဲ့ဒီ process ကိုပြန် run ပြီဆို မှတ်ထားတဲ့ context ကနေ resume ပြန်လုပ်ပေးနိုင်ပါတယ်။ လုပ်တဲ့ steps လေးတွေက ဒီလိုရှိပါတယ်။

-	လက်ရှိ CPU မှာ run နေတဲ့ Process ရဲ့ context ကို save လုပ်ပေးတယ်၊ အဲ့လို save လုပ်တာနဲ့အတူ process မှာရှိတဲ့ PCB block ထဲက တစ်ချို့ value တွေကိုလည်း update လုပ်ပေးပါတယ်။ (P1 လို့ မှတ်ထားလိုက်ပါမယ်)
-	ပြီးတာနဲ့ သူပြောင်းမယ့် state ကိုပြောင်းပြီးတော့ relevant ဖြစ်တဲ့ queue ထဲကိုရောက်သွားတယ်။
-	 နောက် process တစ်ခုကို execute ထပ်လုပ်တယ်။ (P2 လို့မှတ်ထားလိုက်ပါမယ်)
-	 P1 ရဲ့ no 1 and 2 ကအဆင့်တွေလို့ပဲလုပ်ပါတယ်။ ဒီနေရာမှာ memory management data တွေကို update လုပ်ဖို့လိုအပ်လာရင်လည်းလုပ်ပါတယ်။
-	P1 ကို ပြန် execute လုပ်တော့မယ်ဆို မှတ်ထားတဲ့ context တွေ၊ PCB block က data တွေကို reference ပြန်လုပ်ပြီး resume ပြန်လုပ်ပေးနိုင်ပါတယ်။

ဒီလောက်ဆိုရင်တော့ Scheduling ဘယ်လိုအလုပ်လုပ်တယ်ဆိုတာအပြင် သူ့ထဲမှာ ပါတဲ့ modules တွေရဲ့ လုပ်ဆောင်ချက်ကို ကောင်းကောင်းသဘောပေါက်သွားပြီပဲဖြစ်ပါတယ်။
