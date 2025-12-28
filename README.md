# Lyrica_Labs_Nexa_LLM

Nexa, Lyrica Labs tarafından eğitilmiş geniş veri LLM'dir.  
Modellerimizi kullanmak ve API dökümantasyonuna ulaşmak için [Nexa](https://lyricalabs.vercel.app/nexa) bölümüne bakabilirsiniz.

## Kullanım

```python
from lyrica_nexa import NexaClient

client = NexaClient(token="API_TOKENİNİZ")
print(client.list_models())
print(client.generate_text("Merhaba Asya!", model="nexa-5.0-preview"))
