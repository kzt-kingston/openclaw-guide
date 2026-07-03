# OpenClaw အသုံးပြုသူ လက်တွေ့လမ်းညွှန် (Beginner-Friendly Guide)

<img width="1254" height="1254" alt="image" src="https://github.com/user-attachments/assets/79e11c7c-f1d6-4e9d-9cad-1fdd3d20c6bf" />

OpenClaw သည် သင့်စက်ပေါ်တွင် ကိုယ်တိုင် run နိုင်သော (Self-hosted) AI Assistant Gateway တစ်ခု ဖြစ်ပါသည်။ သာမန် Chatbot တစ်ခုထက်ပို၍၊ Telegram, Discord, Slack, WhatsApp ကဲ့သို့သော Messaging App များနှင့် AI Agent များကြားတွင် **Control Center** အဖြစ် ချိတ်ဆက် လုပ်ဆောင်ပေးပါသည်။

---

## 📌 အဓိက အစိတ်အပိုင်းများ (Core Concepts)

OpenClaw ၏ အလုပ်လုပ်ပုံကို နားလည်ရန် အောက်ပါ အစိတ်အပိုင်းများကို သိထားရန် လိုအပ်ပါသည်။

- **Gateway:** OpenClaw ၏ အဓိက အသက်သွေးကြော (Daemon/Process) ဖြစ်ပြီး၊ ၎င်းမရှိဘဲ အခြားလုပ်ဆောင်ချက်များ အလုပ်မလုပ်နိုင်ပါ။
- **Agent:** စဉ်းစားဆင်ခြင်မှုနှင့် လုပ်ဆောင်ချက်များကို တာဝန်ယူသော "ဦးနှောက်" (Runtime) ဖြစ်သည်။
- **Channel:** မက်ဆေ့ချ်များ ဝင်ထွက်ရာ လမ်းကြောင်း (ဥပမာ - Telegram, Discord)။
- **Tool:** AI မှ လက်တွေ့လုပ်ဆောင်နိုင်သော လုပ်ဆောင်ချက်များ (ဥပမာ - `exec`, `browser`, `web_search`)။
- **Skill:** AI အား မည်သည့်အချိန်တွင် မည်သည့် Tool ကို သုံးရမည်ကို သင်ကြားပေးသော လမ်းညွှန် (`SKILL.md`)။
- **Workspace:** Agent အလုပ်လုပ်မည့် ဖိုင်တွဲ (ပုံမှန်အားဖြင့် `~/.openclaw/workspace` တွင်ရှိသည်)။
- **Config:** OpenClaw ၏ ဆက်တင်များ မှတ်သားထားရာ ဖိုင် (`~/.openclaw/openclaw.json`)။

---

## 🚀 စတင် တပ်ဆင်ခြင်း (Installation)

သင့် OS အလိုက် အောက်ပါအတိုင်း တပ်ဆင်နိုင်ပါသည်။ (Node.js လိုအပ်ချက်ကို Installer မှ အလိုအလျောက် ထည့်သွင်းပေးမည် ဖြစ်ပါသည်။)

### Windows (WSL2 ဖြင့် အသုံးပြုရန် အထူး အကြံပြုပါသည်)
Windows တွင် Native ထက် WSL2 သည် ပိုမို တည်ငြိမ်ပါသည်။
1. PowerShell ကို Administrator ဖြင့်ဖွင့်ပြီး `wsl --install` ကို Run ပါ။
2. WSL (ဥပမာ - Ubuntu) အတွင်းသို့ ဝင်ရောက်ပြီး အောက်ပါ Command ဖြင့် တပ်ဆင်ပါ။
   ```bash
   curl -fsSL https://openclaw.ai/install.sh | bash
   ```

### macOS နှင့် Linux
Terminal တွင် အောက်ပါ Command ကို Run ပါ။
```bash
curl -fsSL https://openclaw.ai/install.sh | bash
```

---

## 🏁 ပထမဆုံး အသုံးပြုခြင်း (First Steps)

တပ်ဆင်ပြီးသည်နှင့် အောက်ပါ အဆင့်များအတိုင်း စတင်နိုင်ပါသည်။

1. **Setup ပြုလုပ်ရန်:**
   ```bash
   openclaw onboard --install-daemon
   ```
   *(မှတ်ချက် - Beginner များအနေဖြင့် Local Model ထက် Hosted Provider + API Key ဖြင့် စတင်ခြင်းက ပိုမိုလွယ်ကူပြီး ရလဒ် ပိုကောင်းစေပါသည်။)*

2. **Dashboard မှတစ်ဆင့် စတင် Chat ရန်:**
   ```bash
   openclaw dashboard
   ```
   Browser ပွင့်လာပါက Chat box တွင် `Reply with exactly OPENCLAW-OK.` ဟု ရိုက်ထည့်၍ စမ်းသပ်နိုင်ပါသည်။

---

## 🛠️ ပြဿနာဖြေရှင်းခြင်းနှင့် အသုံးဝင်သော Command များ (Troubleshooting & Useful Commands)

Bot အလုပ်မလုပ်တော့ခြင်း၊ စာပြန်မလာခြင်း၊ သို့မဟုတ် Error တစ်ခုခုတက်ပါက အောက်ပါ Command များကို သုံး၍ ပြဿနာရှာဖွေ ဖြေရှင်းနိုင်ပါသည်။

### 1. `openclaw doctor` (ရောဂါရှာဖွေခြင်း)
- **ဘယ်အချိန်မှာသုံးမလဲ:** စစချင်း ပြဿနာတစ်ခုခုဖြစ်နေသည်ဟု ထင်ပါက (ဥပမာ - Bot စာမပြန်ခြင်း၊ Setup အဆင်မပြေခြင်း) ပထမဆုံး အသုံးပြုရမည့် Command ဖြစ်ပါသည်။
- **ဘာလုပ်ပေးလဲ:** OpenClaw ၏ System Requirements၊ Config အမှားအယွင်းများ၊ Gateway အခြေအနေ နှင့် Channel ချိတ်ဆက်မှု အစရှိသည်တို့ကို တစ်ပြိုင်နက်တည်း အလိုအလျောက် စစ်ဆေးပြီး ပြဿနာရှိသောနေရာကို ထောက်ပြပေးပါသည်။

### 2. `openclaw status` နှင့် `openclaw gateway status`
- **ဘယ်အချိန်မှာသုံးမလဲ:** Gateway (နောက်ကွယ်မှ အဓိက Process) အလုပ် လုပ်/မလုပ် သိချင်သောအခါတွင် သုံးပါသည်။
- **ဘာလုပ်ပေးလဲ:** Gateway run နေသလား၊ သေသွားပြီလား ဆိုသည်ကို ပြသပေးပါသည်။ `openclaw gateway status` သည် ပို၍တိကျသော အခြေအနေကို ဖော်ပြပေးပါသည်။

### 3. `openclaw logs --follow` (မှတ်တမ်းများကြည့်ခြင်း)
- **ဘယ်အချိန်မှာသုံးမလဲ:** Bot ကို စာပို့လိုက်သော်လည်း ဘာကြောင့် စာပြန်မလာသည်ကို နောက်ကွယ်တွင် ဘာတွေဖြစ်နေလဲ (Error များ၊ API ပြဿနာများ) ကို တိုက်ရိုက် ကြည့်ရှုလိုသောအခါ သုံးပါသည်။
- **ဘာလုပ်ပေးလဲ:** လက်ရှိ အချိန်နှင့်တစ်ပြေးညီ (Real-time) OpenClaw ၏ အလုပ်လုပ်နေပုံ၊ Error Message များကို ဖော်ပြပေးပါသည်။ ထွက်လိုပါက `Ctrl + C` ကို နှိပ်ပါ။

### 4. `openclaw gateway restart` (ပြန်လည်စတင်ခြင်း)
- **ဘယ်အချိန်မှာသုံးမလဲ:** ဆက်တင် (Config) အသစ်ပြောင်းလိုက်သောအခါ၊ Bot Error တက်ပြီး ဟန်း (Hang) သွားသောအခါ၊ သို့မဟုတ် Memory အသုံးပြုမှုများနေ၍ ရှင်းလင်းလိုသောအခါ သုံးပါသည်။
- **ဘာလုပ်ပေးလဲ:** OpenClaw Gateway ကို ပိတ်ပြီး အသစ် ပြန်ဖွင့်ပေးပါသည်။

### 5. `openclaw config validate` (ဆက်တင် မှန်/မမှန် စစ်ဆေးခြင်း)
- **ဘယ်အချိန်မှာသုံးမလဲ:** `openclaw.json` (ဆက်တင်ဖိုင်) တွင် Token ထည့်ခြင်း၊ ပြင်ဆင်ခြင်းများ ပြုလုပ်ပြီးနောက် စာလုံးပေါင်း အမှားအယွင်း ရှိ/မရှိ စစ်ဆေးလိုသောအခါ သုံးပါသည်။
- **ဘာလုပ်ပေးလဲ:** ဆက်တင်ဖိုင်ထဲတွင် JSON format မှားယွင်းနေခြင်း၊ မပါဝင်ရမည့် အချက်များ ပါနေခြင်းတို့ကို ထောက်ပြပေးပါသည်။

---

## 🔗 ချန်နယ်များ ချိတ်ဆက်ခြင်း (Connecting Channels)

OpenClaw ကို သင့်စိတ်ကြိုက် Messaging App များနှင့် ချိတ်ဆက်နိုင်ပါသည်။

### Discord ဖြင့် ချိတ်ဆက်ခြင်း

Discord ပေါ်တွင် OpenClaw ကို အသုံးပြုရန်အတွက် သင့်ကိုယ်ပိုင် Private Server တစ်ခု ဖန်တီးပြီး ထို Server ထဲသို့ Bot အား ထည့်သွင်းရန် အကြံပြုပါသည်။

**အဆင့် (၁): Discord Bot ဖန်တီးခြင်း**
1. [Discord Developer Portal](https://discord.com/developers/applications) သို့သွားပြီး **New Application** ကိုနှိပ်ကာ နာမည်ပေးပါ။
2. ဘယ်ဘက် Menu မှ **Bot** ကိုရွေးပြီး သင့် Agent အတွက် နာမည်တစ်ခု ပေးပါ။
3. ထိုစာမျက်နှာအောက်ရှိ **Privileged Gateway Intents** တွင် အောက်ပါတို့ကို ဖွင့်ပေးပါ-
   - **Message Content Intent** (မဖြစ်မနေ ဖွင့်ရမည်)
   - **Server Members Intent** (အကြံပြုသည်)
4. အပေါ်သို့ ပြန်တက်၍ **Reset Token** ကိုနှိပ်ပြီး ထွက်လာသော **Bot Token** ကို သေချာစွာ သိမ်းဆည်းထားပါ။ (၎င်းသည် သင့် Bot ၏ သော့ချက် ဖြစ်သည်)

**အဆင့် (၂): Bot ကို သင့် Server ထဲသို့ ထည့်ခြင်း**
1. ဘယ်ဘက် Menu မှ **OAuth2** ကိုနှိပ်ပါ။
2. အောက်ဘက်ရှိ **OAuth2 URL Generator** တွင် `bot` နှင့် `applications.commands` ကို အမှန်ခြစ်ပါ။
3. အောက်တွင်ပေါ်လာသော **Bot Permissions** တွင် အောက်ပါတို့ကို အမှန်ခြစ်ပါ-
   - View Channels
   - Send Messages
   - Read Message History
   - Embed Links
   - Attach Files
4. အောက်ဆုံးရှိ URL ကို Copy ကူးပြီး Browser တွင်ဖွင့်ကာ သင့် Server ထဲသို့ Bot ကို ထည့်သွင်းပါ။

**အဆင့် (၃): Developer Mode ဖွင့်ခြင်း (ID များ ရယူရန်)**
1. Discord App ၏ **User Settings** (ဂီယာခလုတ်) → **Advanced** တွင် **Developer Mode** ကိုဖွင့်ပါ။
2. သင့် Server Icon ကို Right-click ထောက်ပြီး **Copy Server ID** ကိုနှိပ်၍ သိမ်းထားပါ။
3. သင့် ကိုယ်ပိုင် Avatar ကို Right-click ထောက်ပြီး **Copy User ID** ကိုနှိပ်၍ သိမ်းထားပါ။

**အဆင့် (၄): OpenClaw ဘက်တွင် ဆက်တင်ထည့်ခြင်း**
Terminal တွင် အောက်ပါ Command များကို Run ပါ (YOUR_BOT_TOKEN နေရာတွင် သင့် Bot Token ကို အစားထိုးပါ)-

```bash
export DISCORD_BOT_TOKEN="YOUR_BOT_TOKEN"
openclaw config set channels.discord.token --ref-provider default --ref-source env --ref-id DISCORD_BOT_TOKEN
openclaw config set channels.discord.enabled true
openclaw gateway restart
```

**အဆင့် (၅): ချိတ်ဆက်မှုကို အတည်ပြုခြင်း (Pairing)**
1. သင့် Discord Server ထဲရှိ Bot ထံသို့ တိုက်ရိုက် (DM ဖြင့်) မက်ဆေ့ချ် တစ်ခုခု ပို့လိုက်ပါ။
2. Bot မှ သင့်အား **Pairing Code** (ဂဏန်း/စာလုံးများ) ပြန်ပို့ပေးပါလိမ့်မည်။
3. Terminal တွင် အောက်ပါ Command ဖြင့် အတည်ပြုပါ-
   ```bash
   openclaw pairing approve discord <code>
   ```

*(ယခုအခါ Discord တွင် OpenClaw Agent နှင့် စတင် စကားပြောနိုင်ပြီ ဖြစ်ပါသည်။ Guild (Server Channels) များတွင် အသုံးပြုလိုပါက Allowlist ဆက်တင်များ ထပ်မံ ထည့်သွင်းရန် လိုအပ်နိုင်ပါသည်။)*

### Telegram ဖြင့် ချိတ်ဆက်ခြင်း

Telegram တွင် အသုံးပြုရန် Bot အသစ်တစ်ခု ဖန်တီးပြီး ချိတ်ဆက်နိုင်ပါသည်။

**အဆင့် (၁): BotFather မှတစ်ဆင့် Bot ဖန်တီးခြင်း**
1. Telegram တွင် **@BotFather** ကိုရှာဖွေပြီး `Start` နှိပ်ပါ။
2. `/newbot` ဟုရိုက်ထည့်ပြီး Bot အတွက် နာမည် နှင့် Username ကို ပေးပါ။
3. BotFather မှပေးလာသော **Bot Token** ကို သေချာစွာ သိမ်းဆည်းထားပါ။

**အဆင့် (၂): OpenClaw ဘက်တွင် ဆက်တင်ထည့်ခြင်း**
Terminal တွင် အောက်ပါ Command များကို Run ပါ (YOUR_BOT_TOKEN နေရာတွင် သင့် Bot Token ကို အစားထိုးပါ)-

```bash
export TELEGRAM_BOT_TOKEN="YOUR_BOT_TOKEN"
openclaw config set channels.telegram.token --ref-provider default --ref-source env --ref-id TELEGRAM_BOT_TOKEN
openclaw config set channels.telegram.enabled true
```

**အဆင့် (၃): ချိတ်ဆက်မှုကို အတည်ပြုခြင်း (Pairing)**
1. Gateway ကို စတင်ပါ-
   ```bash
   openclaw gateway
   ```
2. Terminal တွင် Pairing Code ကို စစ်ဆေးပါ-
   ```bash
   openclaw pairing list telegram
   ```
3. သင့် Telegram Bot ဆီသို့ တိုက်ရိုက် (DM ဖြင့်) သွားပြီး စကားပြောကြည့်ပါ။ ထို့နောက် Terminal တွင် အောက်ပါအတိုင်း အတည်ပြုပါ-
   ```bash
   openclaw pairing approve telegram <code>
   ```

*(Telegram Group များတွင် ထည့်သွင်း အသုံးပြုလိုပါက Bot ကို Group ထဲသို့ ထည့်ပြီးနောက် OpenClaw config ဖိုင်တွင် `groupPolicy` နှင့် `allowFrom` ဆက်တင်များ ပြင်ဆင်ရန် လိုအပ်နိုင်ပါသည်။)*

---

## 🤖 ရရှိနိုင်သော AI Model ၂၀ မျိုး နှင့် ချိတ်ဆက်အသုံးပြုနည်းများ (၂၀၂၆ Update)

OpenClaw တွင် အခမဲ့ (Free) မှစ၍ အခကြေးငွေပေးရသော (Premium) AI Model များအထိ စိတ်ကြိုက် ချိတ်ဆက် အသုံးပြုနိုင်ပါသည်။ အောက်ပါတို့မှာ ၂၀၂၆ ခုနှစ်အတွက် အကောင်းဆုံး Model ၂၀ ခုနှင့် ၎င်းတို့၏ API Key များ ရယူနည်းများ ဖြစ်ပါသည်။

### 🌟 အခမဲ့ နှင့် ဈေးသက်သာသော Model များ (Free / Budget-Friendly)

**၁။ DeepSeek V4 Preview**
- **အကျဉ်းချုပ်:** လက်ရှိ ၂၀၂၆ တွင် အခမဲ့/ဈေးသက်သာသော Model များထဲ၌ အကောင်းဆုံး (Reasoning & Coding) ဖြစ်ပါသည်။
- **API ရယူရန်:** [DeepSeek Platform](https://platform.deepseek.com/) တွင် အကောင့်ဖွင့်၍ Key ယူပါ။
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set providers.deepseek.apiKey "YOUR_API_KEY"
  openclaw config set agents.defaults.model "deepseek/deepseek-v4-preview"
  ```

**၂။ DeepSeek V3**
- **အကျဉ်းချုပ်:** ယခင် မျိုးဆက်ဖြစ်သော်လည်း အလွန်မြန်ဆန်ပြီး ဈေးနှုန်း အလွန်သက်သာပါသည်။
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set agents.defaults.model "deepseek/deepseek-chat"
  ```

**၃။ Gemini 3.1 Flash (Google)**
- **အကျဉ်းချုပ်:** Google ၏ မျိုးဆက်သစ် Model ဖြစ်ပြီး အမြန်နှုန်းနှင့် Free Tier (အခမဲ့) ပေးထားမှုကြောင့် အလွန်ရေပန်းစားသည်။
- **API ရယူရန်:** [Google AI Studio](https://aistudio.google.com/) သို့သွား၍ "Get API key" ကိုနှိပ်ပါ။
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set providers.google.apiKey "YOUR_API_KEY"
  openclaw config set agents.defaults.model "google/gemini-3.1-flash"
  ```

**၄။ Gemini 3.1 Flash-Lite**
- **အကျဉ်းချုပ်:** ပို၍ပေါ့ပါးပြီး မြန်ဆန်သော Model ဖြစ်ကာ ရိုးရှင်းသည့် မေးခွန်းများအတွက် အထူးကောင်းမွန်သည်။
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set agents.defaults.model "google/gemini-3.1-flash-lite"
  ```

**၅။ LLaMA 4 Scout (Meta via Groq/OpenRouter)**
- **အကျဉ်းချုပ်:** Meta ၏ အသစ်ဆုံး Open-weight Model ဖြစ်ပြီး Context အလွန်ရှည်လျားစွာ (10M အထိ) မှတ်သားနိုင်ပါသည်။
- **API ရယူရန်:** [OpenRouter](https://openrouter.ai/) တွင် LLaMA 4 ကို ရွေးချယ်နိုင်ပါသည်။
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set providers.openrouter.apiKey "YOUR_API_KEY"
  openclaw config set agents.defaults.model "openrouter/meta-llama/llama-4-scout"
  ```

**၆။ LLaMA 4 (Meta)**
- **အကျဉ်းချုပ်:** LLaMA 4 ၏ Standard Version ဖြစ်ပြီး General Tasks များအတွက် သင့်တော်ပါသည်။
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set agents.defaults.model "openrouter/meta-llama/llama-4"
  ```

**၇။ Gemma 4 (Google)**
- **အကျဉ်းချုပ်:** Google ၏ Open-weight Model အသစ်ဖြစ်ပြီး Coding နှင့် ကျိုးကြောင်းဆင်ခြင်ရာတွင် အထူးကောင်းမွန်သည်။
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set agents.defaults.model "google/gemma-4"
  ```

**၈။ Groq LLaMA / Mixtral**
- **အကျဉ်းချုပ်:** Groq ၏ LPU ဖြင့် အလုပ်လုပ်သောကြောင့် တစ်စက္ကန့်လျှင် စကားလုံးရာချီ ထုတ်ပေးနိုင်သော အမြန်ဆုံး API ဖြစ်ပါသည်။
- **API ရယူရန်:** [GroqCloud](https://console.groq.com/keys)
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set providers.groq.apiKey "YOUR_API_KEY"
  openclaw config set agents.defaults.model "groq/llama3-70b-8192"
  ```

**၉။ Qwen 3 (Alibaba)**
- **အကျဉ်းချုပ်:** Alibaba ၏ နောက်ဆုံးထွက် Model ဖြစ်ပြီး ဘာသာစကားမျိုးစုံနှင့် Multimodal အတွက် အလွန်ကောင်းမွန်ပါသည်။
- **OpenClaw တွင်ထည့်ရန်:** OpenRouter မှတစ်ဆင့် သုံးနိုင်ပါသည်။
  ```bash
  openclaw config set agents.defaults.model "openrouter/qwen/qwen-3"
  ```

**၁၀။ OpenRouter Free Models (Aggregator)**
- **အကျဉ်းချုပ်:** Model ပေါင်းစုံကို Free Tier ဖြင့် ခေါ်သုံးနိုင်သော API တစ်ခုတည်းဖြစ်ပါသည်။
- **API ရယူရန်:** [OpenRouter](https://openrouter.ai/)
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set providers.openrouter.apiKey "YOUR_API_KEY"
  openclaw config set agents.defaults.model "openrouter/meta-llama/llama-3-8b-instruct:free"
  ```

### 💎 အဆင့်မြင့် Premium Model များ (High-End / Paid)

**၁၁။ GPT-5.5 (OpenAI)**
- **အကျဉ်းချုပ်:** OpenAI ၏ ၂၀၂၆ နောက်ဆုံးထွက် Flagship Model ဖြစ်ပြီး Agentic Coding နှင့် သိပ္ပံနည်းကျ သုတေသနလုပ်ငန်းများတွင် အကောင်းဆုံးဖြစ်ပါသည်။
- **API ရယူရန်:** [OpenAI Platform](https://platform.openai.com/api-keys)
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set providers.openai.apiKey "YOUR_API_KEY"
  openclaw config set agents.defaults.model "openai/gpt-5.5"
  ```

**၁၂။ GPT-5.4 (OpenAI)**
- **အကျဉ်းချုပ်:** ယခင် Update Model ဖြစ်ပြီး Professional Knowledge Work အတွက် အလွန်အားထားရပါသည်။
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set agents.defaults.model "openai/gpt-5.4"
  ```

**၁၃။ Claude Opus 4.7 (Anthropic)**
- **အကျဉ်းချုပ်:** ၂၀၂၆ ဧပြီလတွင် ထွက်ရှိသော Model အသစ်ဖြစ်ပြီး ရှုပ်ထွေးသော စဉ်းစားဆင်ခြင်မှုများနှင့် Software Engineering အတွက် နံပါတ် ၁ နေရာတွင် ရှိနေပါသည်။
- **API ရယူရန်:** [Anthropic Console](https://console.anthropic.com/)
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set providers.anthropic.apiKey "YOUR_API_KEY"
  openclaw config set agents.defaults.model "anthropic/claude-opus-4-7"
  ```

**၁၄။ Claude Sonnet 4.6 (Anthropic)**
- **အကျဉ်းချုပ်:** အလုပ်လုပ်နှုန်းမြန်ဆန်ပြီး နေ့စဉ် Coding နှင့် စာရေးသားရာတွင် အကောင်းဆုံး Workhorse Model ဖြစ်ပါသည်။
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set agents.defaults.model "anthropic/claude-sonnet-4-6"
  ```

**၁၅။ Gemini 3.1 Pro (Google)**
- **အကျဉ်းချုပ်:** Google ၏ Premium Model ဖြစ်ပြီး Multi-modal (ရုပ်ပုံ၊ အသံ၊ စာ) ပေါင်းစပ်ခွဲခြမ်းစိတ်ဖြာရာတွင် အထူးကောင်းမွန်သည်။
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set providers.google.apiKey "YOUR_API_KEY"
  openclaw config set agents.defaults.model "google/gemini-3.1-pro"
  ```

**၁၆။ Grok 4 (xAI)**
- **အကျဉ်းချုပ်:** X (Twitter) အချက်အလက်များကို Real-time ရယူနိုင်ပြီး Native Tool အသုံးပြုမှုများတွင် အလွန်ကောင်းမွန်သည်။
- **API ရယူရန်:** [X.AI Console](https://console.x.ai/)
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set providers.xai.apiKey "YOUR_API_KEY"
  openclaw config set agents.defaults.model "xai/grok-4"
  ```

**၁၇။ Mistral Large 3 (Mistral AI)**
- **အကျဉ်းချုပ်:** ဥရောပမှ ထိပ်တန်း Open-weight Model အကြီးစားဖြစ်ပြီး ဘာသာစကားကျွမ်းကျင်မှု အလွန်မြင့်မားသည်။
- **API ရယူရန်:** [Mistral Platform](https://console.mistral.ai/)
- **OpenClaw တွင်ထည့်ရန်:**
  ```bash
  openclaw config set providers.mistral.apiKey "YOUR_API_KEY"
  openclaw config set agents.defaults.model "mistral/mistral-large-3"
  ```

**၁၈။ Muse Spark (Meta)**
- **အကျဉ်းချုပ်:** Meta ၏ စီးပွားရေးလုပ်ငန်းသုံး Managed API အသစ်ဖြစ်ပြီး Multi-agent Orchestration အတွက် အလွန်ကောင်းမွန်သည်။
- **API ရယူရန်:** Meta API Gateway မှတစ်ဆင့် ရယူနိုင်ပါသည်။

**၁၉။ Zhipu GLM-5.1**
- **အကျဉ်းချုပ်:** ရှည်လျားသော Software Development Task များနှင့် Agentic Engineering အတွက် အထူးထုတ်လုပ်ထားသော Model ဖြစ်ပါသည်။
- **OpenClaw တွင်ထည့်ရန်:** OpenRouter မှတစ်ဆင့် အသုံးပြုရန် အကြံပြုပါသည်။
  ```bash
  openclaw config set agents.defaults.model "openrouter/zhipu/glm-5.1"
  ```

**၂၀။ Moonshot Kimi K2.6**
- **အကျဉ်းချုပ်:** Context Window အလွန်ရှည်လျားပြီး Coding နှင့် Customer Support လုပ်ငန်းများအတွက် သင့်တော်ပါသည်။
- **OpenClaw တွင်ထည့်ရန်:** OpenRouter မှတစ်ဆင့် အသုံးပြုရန် အကြံပြုပါသည်။
  ```bash
  openclaw config set agents.defaults.model "openrouter/moonshot/kimi-k2.6"
  ```

*(မှတ်ချက် - API Key များ ထည့်သွင်းပြီးတိုင်း Gateway ကို `openclaw gateway restart` ဖြင့် Restart ချပေးရန် လိုအပ်ပါသည်။)*

---

## ⏰ အလိုအလျောက် ခိုင်းစေခြင်း (Cron Jobs Automation)

OpenClaw ကို Chatbot အဖြစ်သာမက အချိန်နှင့်အမျှ အလိုအလျောက် အလုပ်လုပ်ပေးသော Assistant အဖြစ်ပါ အသုံးပြုနိုင်ပါသည်။

**ဥပမာ - နေ့စဉ် မနက် ၇ နာရီတိုင်း အကျဉ်းချုပ် တောင်းခံခြင်း:**
```bash
openclaw cron add \
  --name "Morning brief" \
  --cron "0 7 * * *" \
  --tz "Asia/Bangkok" \
  --session isolated \
  --message "Summarize today's calendar and top priorities." \
  --announce
```

**Cron များကို စီမံရန်:**
- ကြည့်ရှုရန်: `openclaw cron list`
- ဖျက်ရန်/ရပ်ရန်: `openclaw cron disable <job-id>`

---

## 🛡️ လုံခြုံရေးဆိုင်ရာ အကောင်းဆုံး အလေ့အကျင့်များ (Security Best Practices)

- **Dashboard ကို Public မဖွင့်ပါနှင့်:** Localhost (သို့) Secure Tunnel ဖြင့်သာ အသုံးပြုပါ။
- **စကားဝှက် ခိုင်မာစွာ ထားပါ:** Dashboard အတွက် Strong Password သုံးပါ။
- **Workspace သန့်ရှင်းမှု:** လျှို့ဝှက် အချက်အလက်များ (Secrets/Passwords) ကို Workspace အတွင်း ရေးမထားပါနှင့်။ Environment Variables များကိုသာ သုံးပါ။
- **စောင့်ကြည့် စစ်ဆေးပါ:** `openclaw logs --follow` နှင့် `openclaw doctor` ကို အသုံးပြု၍ ပုံမှန် စစ်ဆေးပါ။

---

## 💻 စက်ပစ္စည်း လိုအပ်ချက်များ (Hardware Requirements)

- **Gateway သီးသန့်နှင့် API အသုံးပြုရန်:** 2 vCPU, 4 GB RAM (အနည်းဆုံး) | 4 vCPU, 8 GB RAM (အကြံပြုချက်)
- **Ollama ဖြင့် Local Model သုံးရန်:** 16 GB မှ 32 GB RAM / GPU လိုအပ်နိုင်ပါသည်။ Beginner များအတွက် Hosted APIs များကို အသုံးပြုခြင်းက ပိုမို အဆင်ပြေစေပါသည်။

---

## 📚 ထပ်မံလေ့လာရန် (Further Resources)

- [Official Getting Started Guide](https://docs.openclaw.ai/start/getting-started)
- [Official CLI Reference](https://docs.openclaw.ai)
- အခက်အခဲ တစ်စုံတစ်ရာ ရှိပါက `openclaw doctor` ကို အမြဲတမ်း အရင်ဆုံး အသုံးပြုပါ။

---

<p align="center">
  <sub>
    <i>Documentation snapshot: 29 April 2026</i><br>
    Reflects the project as of this date; later changes may not be documented.
  </sub>
</p>