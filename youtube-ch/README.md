# Stage 1: Niche Architecture & Data Collection (Claude)
First, we turn Claude into a YouTube analytics expert. To maximize profit, we target the US or European markets due to higher 
CPM (payout per 1,000 views).

## What to do:
Open Claude.ai.

Use this Prompt:
```
"Act as an expert YouTube Analyst. Analyze the 'AI Tools for Productivity' niche for the US market. Create a content plan of 10 videos. For the first video, write a detailed 8-minute script.

The script must include: 
1. Narrator text. 
2. Visual instructions in brackets [ ].
3. AI image generation prompts for each block. Output the result in JSON format where keys are scene numbers."
```

# Stage 2: Asset Automation (Python)
To avoid manually copying text into voiceover services, we use Python. This saves 2–3 hours per video.

## What to do:
Get an API key from ElevenLabs.
Install the library: pip install requests.
Create a file named voiceover.py and insert this code:

```python
import requests

API_KEY = "YOUR_API_KEY"
VOICE_ID = "pNInz6obpgDQGcFmaJgB" # Choose a high-quality Voice ID from ElevenLabs

def generate_audio(text, filename):
    url = f"https://api.elevenlabs.io/v1/text-to-speech/{VOICE_ID}"
    headers = {"xi-api-key": API_KEY, "Content-Type": "application/json"}
    data = {
        "text": text,
        "model_id": "eleven_multilingual_v2",
        "voice_settings": {"stability": 0.5, "similarity_boost": 0.8}
    }
    response = requests.post(url, json=data, headers=headers)
    with open(f"{filename}.mp3", "wb") as f:
        f.write(response.content)
    print(f"Done: {filename}.mp3")

# Insert script segments from Claude here
generate_audio("Welcome to the future of productivity...", "intro")
```

# Stage 3: Visual Preparation (Python + AI)
If you don't want to hunt for stock footage, use Python for mass image generation via the OpenAI DALL-E 3 API. 
--> Via Microsoft Designer (Free of Charge)

## Mass Generation Code (image_gen.py):
```python
import openai

openai.api_key = "YOUR_OPENAI_KEY"

prompts = [
    "Futuristic office with holograms, 8k, cinematic lighting",
    "A person using a neural interface, cyberpunk style"
]

for i, p in enumerate(prompts):
    response = openai.Image.create(prompt=p, n=1, size="1024x1024")
    print(f"Image {i} ready: {response['data'][0]['url']}")
```

# Stage 4: High-Speed Editing (Premiere Pro 2026)
Now you have a folder with audio and a folder with images/video. In 2026, Premiere Pro handles 80% of the manual labor.

## Step-by-step actions:
Import: Drag all assets into the project.
Text-Based Editing: Go to Window -> Text. Premiere scans your voiceover and turns it into text. You can edit the video by simply 
deleting unnecessary words in the text editor!

AI Enhance Speech: Select audio -> Essential Sound -> Enhance. This makes the AI voice indistinguishable from a studio recording.

Auto Reframe: To create "Shorts" from a long video (increasing your reach), right-click the Sequence -> Auto Reframe Sequence. The 
AI will keep objects centered in the vertical frame.

# Stage 5: Cashing Out (Monetization Strategy)
Uploading the video is only half the battle. You need to make it work for your wallet.

- Affiliate Links: Ask Claude: "Find 3 affiliate programs for the tools mentioned in the script." Insert these links in the description. 
In the AI niche, commissions can be $20+ per sale.
- YouTube AdSense: Requires 1,000 subscribers. To get there fast, produce 1 long video and 5 Shorts from it every week.
- Claude for SEO:
    - Prompt: "Write a headline with a CTR over 10% and a video description using keywords: [your keywords]. Provide 5 text options for the thumbnail."

# Why is this formula "Money"?
Claude eliminates "writer's block."
Python automates the drudgery (no more clicking "download" 50 times).
Premiere Pro packages everything into a high-quality product that advertisers pay for.

# Where to start right now?
Get your ElevenLabs API key.
Ask Claude to pick a niche.
Run your first voiceover script.
