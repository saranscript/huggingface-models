from transformers import pipeline
import json
import requests

API_URL = "https://api-inference.huggingface.co/models/EleutherAI/gpt-neo-2.7B"
headers = {"Authorization": "Bearer api_hwKbAMoHAzOVDdCxgfpPxMjjcrdKHMakhg"}

def query(payload):
\tdata = json.dumps(payload)
\tresponse = requests.request("POST", API_URL, headers=headers, data=data)
\treturn json.loads(response.content.decode("utf-8"))

data = query("Can you please let us know more details about your ")