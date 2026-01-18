from openai import OpenAI
class api():

API_KEY = "pplx-your_api_key_here"

client = OpenAI(
    api_key=API_KEY,
    base_url="https://api.perplexity.ai"
)

messages = [
    {
        "role": "system",
        "content": "Ты полезный ассистент, отвечай кратко и точно."
    },
    {
        "role": "user",
        "content": "Расскажи о API Perplexity."
    }
]

response = client.chat.completions.create(
    model="sonar-small-online",  # Или "sonar-pro", "llama-3.1-sonar-small-128k-online"
    messages=messages,
    max_tokens=1024,
    temperature=0.1,
    stream=False
)

print("Ответ:", response.choices[0].message.content)
print("Использовано токенов:", response.usage.total_tokens)

