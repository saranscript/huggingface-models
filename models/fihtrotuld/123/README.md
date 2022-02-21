import requests

API_URL = "https://api-inference.huggingface.co/models/huggingface/prunebert-base-uncased-6-finepruned-w-distil-squad"
headers = {"Authorization": "Bearer api_UXqrzQBiZKXaWxstVwEKcYvHQpGSGiQGbr"}

def query(payload):
	response = requests.post(API_URL, headers=headers, json=payload)
	return response.json()

output = query({
    "inputs": {
		"question": "What's my name?",
		"context": "My name is Clara and I live in Berkeley.",
	},
})