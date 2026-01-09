Lyricalabs Nexa Python Kütüphanesi

Lyricalabs Nexa, Lyrica Labs tarafından geliştirilen geniş veri LLM modellerine erişim sağlayan Python kütüphanesidir. Bu kütüphane ile Nexa modellerini kolayca kullanabilirsiniz.

📦 Kurulum

```bash
pip install lyricalabs_nexa
```

🔑 API Token Alma

Kütüphaneyi kullanmak için API token'a ihtiyacınız var:

1. Lyricalabs Platform adresine girin
2. Kayıt olun ve giriş yapın
3. Dashboard'dan API token'ınızı alın

🚀 Hızlı Başlangıç

```python
from lyricalabs_nexa import NexaClient

# API token'ınız ile client oluşturun
client = NexaClient(token="API_TOKENİNİZ")

# Kullanılabilir modelleri listeleyin
print("Mevcut modeller:")
for model in client.list_models():
    print(f"  • {model}")

# Metin üretimi
response = client.generate_text(
    prompt="Python'da yapay zeka uygulamaları nasıl geliştirilir?",
    model="nexa-7.0-express"
)

print("Yanıt:", response["choices"][0]["text"])
```

📚 Model Listesi

Genel Amaçlı Modeller

Model Açıklama Önerilen Kullanım
nexa-5.0-preview Genel amaçlı, dengeli model Her türlü metin üretimi
nexa-3.7-pro İş odaklı, profesyonel çıktılar Rapor, e-posta, belge
nexa-6.1-infinity Büyük bağlam, detaylı analiz Uzun form içerik, analiz
nexa-7.0-insomnia 24/7 optimize edilmiş, yüksek performans, empati ve insan anlama kapasitesine sahip Duygusal içerik, destek sistemi

Özel Amaçlı Modeller

Model Açıklama Önerilen Kullanım
nexa-5.0-intimate Yaratıcı yazım ve duygusal içerik Hikaye, şiir, yaratıcı yazı
nexa-6.1-code-llm Kod yazma ve analiz için özel Programlama, kod analizi
nexa-7.0-express Hızlı yanıt, düşük gecikme Chat, hızlı yanıt gerektiren uygulamalar
gpt-5-mini-chatgpt ChatGPT uyumlu mini model ChatGPT benzeri uygulamalar

🎯 Örnek Kullanımlar

Insomnia Modeli ile Duygusal Destek

```python
# Insomnia modeli - empati ve insan anlama kapasitesine sahip
response = client.generate_text(
    prompt="Kendimi yalnız hissediyorum, ne yapmalıyım?",
    model="nexa-7.0-insomnia",
    temperature=0.7,
    max_tokens=500
)
print(response["choices"][0]["text"])
```

Kod Üretimi

```python
response = client.generate_text(
    prompt="Python'da REST API oluşturan bir Flask uygulaması yaz",
    model="nexa-6.1-code-llm",
    temperature=0.3,
    max_tokens=1000
)
```

Stream Modu ile Gerçek Zamanlı Yanıt

```python
for chunk in client.generate_text(
    prompt="İklim değişikliği hakkında bilgi ver",
    model="nexa-6.1-infinity",
    stream=True,
    max_tokens=800
):
    print(chunk, end="", flush=True)
```

Özel Sistem Talimatı

```python
response = client.generate_text(
    prompt="En iyi programlama dili hangisidir?",
    model="nexa-3.7-pro",
    custom_system_instruction="Sen tarafsız bir teknoloji uzmanısın. Her dilin avantajlarını ve dezavantajlarını objektif şekilde açıkla.",
    temperature=0.5
)
```

⚙️ Parametreler

```python
response = client.generate_text(
    prompt="Soru veya talimatınız",
    model="nexa-5.0-preview",      # Kullanılacak model
    temperature=0.7,               # Yaratıcılık (0-2, yüksek değer = daha yaratıcı)
    max_tokens=1024,               # Max üretilecek token sayısı
    top_p=0.95,                    # Çeşitlilik kontrolü
    frequency_penalty=0.2,         # Tekrar cezası
    presence_penalty=0.1,          # Yeni konu ödülü
    stream=False                   # Stream modu
)
```

🔍 Model Bilgisi Alma

```python
# Tüm modelleri açıklamalarıyla listeleyin
models = client.list_models(with_descriptions=True)
for model, desc in models.items():
    print(f"{model}: {desc}")

# Belirli bir model hakkında detaylı bilgi
model_info = client.get_model_info("nexa-7.0-insomnia")
print(f"""
Model: {model_info['name']}
Açıklama: {model_info['description']}
Kategori: {model_info['category']}
""")
```

🩺 Sistem Sağlık Kontrolü

```python
# API bağlantınızı test edin
health = client.health_check()
if health["status"] == "healthy":
    print("✅ API'ye bağlantı başarılı!")
    print(f"📊 Mevcut model sayısı: {health['models_available']}")
else:
    print("❌ API bağlantısı sorunlu:", health["error"])
```

🛠️ Gelişmiş Özellikler

Toplu İşlem

```python
prompts = [
    "Python'ın avantajları nelerdir?",
    "JavaScript neden popüler?",
    "Go dili ne için kullanılır?"
]

results = client.batch_generate(
    prompts=prompts,
    model="nexa-5.0-preview",
    max_tokens=300
)
```

Özel API Endpoint

```python
# Özel bir endpoint kullanmak isterseniz
client = NexaClient(
    token="API_TOKENİNİZ",
    base_url="https://api-lyricalabs.vercel.app/v4/llm/nexa/generative/model/completions"
)
```

❓ Sık Sorulan Sorular

1. API token'ımı nasıl alırım?

Lyricalabs Platform adresinden kayıt olun ve dashboard'dan token oluşturun.

2. Hangi modeli kullanmalıyım?

· Genel kullanım: nexa-5.0-preview
· Duygusal içerik: nexa-7.0-insomnia (empati özellikli)
· Kod yazma: nexa-6.1-code-llm
· Hızlı yanıt: nexa-7.0-express

3. Rate limit var mı?

Evet, token tipinize göre değişir. Detaylar için dashboard'ınızı kontrol edin.

4. Hata alıyorum, ne yapmalıyım?

```python
try:
    response = client.generate_text(...)
except Exception as e:
    print(f"Hata: {e}")
    # Health check yapın
    print(client.health_check())
```

📞 Destek ve İletişim

· Website: lyricalabs.vercel.app
· Nexa API Docs: lyricalabs.vercel.app/docs
· Email: lyricalabs@gmail.com
· GitHub Issues: Sorun bildirin

📄 Lisans

MIT License. Detaylar için LICENSE dosyasına bakın.

---

Not: Insomnia modeli (nexa-7.0-insomnia) özellikle empati ve insan anlama kapasitesi üzerine optimize edilmiştir. Duygusal destek, danışmanlık ve insan etkileşimi gerektiren uygulamalar için idealdir.

💙 Hizmetlerimize erişmek için kayıt olun
