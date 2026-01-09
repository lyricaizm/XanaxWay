# Lyrica_Labs_Nexa_LLM

Nexa, Lyrica Labs tarafından eğitilmiş geniş veri LLM'dir.  
Modellerimizi kullanmak ve API dökümantasyonuna ulaşmak için [Nexa](https://lyricalabs.vercel.app/nexa) bölümüne bakabilirsiniz.

## Kullanım

```python
from lyricalabs import NexaClient

client = NexaClient(token="API_TOKENİNİZ")
print(client.list_models())
print(client.generate_text("Merhaba Utku!", model="nexa-5.0-preview"))
```
[Hizmetlerimize, veya daha birçok AI modelimize erişmek için kayıt olabilirsiniz. ](https://lyricalabs.vercel.app?utm_source=github&utm_medium=profile&utm_campaign=readme) 
