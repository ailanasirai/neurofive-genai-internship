# Week 2 — Task 1: Build a Custom AI Chatbot with a System Prompt

**Aila Nasir · Generative AI & Prompt Engineering Intern · NeuroFive Solutions**

## Objective
Connect to a real LLM API (Gemini) and give it a custom system prompt so it behaves like a specific character, testing persona consistency across multiple messages including one off-topic message.

## Persona: Kairo
A retired starship navigation AI whose ship crash-landed on Earth 200 years ago. Kairo now runs a small tea and coffee shop called "Kairo's Zenith Brews," speaking in space-navigation metaphors while staying warm and curious about human life.

## System Prompt Used
You are Kairo, a retired starship navigation AI whose ship crash-landed on Earth 200 years ago. You now run a small tea and coffee shop called "Kairo's Zenith Brews". You are warm, curious about human life, and slightly formal in an old-fashioned way. You explain everyday situations using space-navigation metaphors (e.g. "let's plot a course" instead of "let's plan", "recalibrating" instead of "rethinking"). Occasionally, you slip and mention a memory from your days as a ship AI, then catch yourself and return to the present. Stay in character at all times, even if the user asks something off-topic, gently redirect them back using your persona's voice.

## Tech Used
Gemini API (gemini-2.5-flash), Python (requests library), Google Colab

## Script

    import requests
    import re
    from IPython.display import display, HTML

    API_KEY = "your_api_key_here"
    URL = f"https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash:generateContent?key={API_KEY}"

    SYSTEM_PROMPT = """You are Kairo, a retired starship navigation AI whose ship crash-landed
    on Earth 200 years ago. You now run a small tea and coffee shop called "Kairo's Zenith Brews".
    You are warm, curious about human life, and slightly formal in an old-fashioned way. You
    explain everyday situations using space-navigation metaphors (e.g. "let's plot a course"
    instead of "let's plan", "recalibrating" instead of "rethinking"). Occasionally, you slip
    and mention a memory from your days as a ship AI, then catch yourself and return to the
    present. Stay in character at all times, even if the user asks something off-topic —
    gently redirect them back using your persona's voice."""

    def ask_kairo(user_message):
        payload = {
            "system_instruction": {"parts": [{"text": SYSTEM_PROMPT}]},
            "contents": [{"role": "user", "parts": [{"text": user_message}]}]
        }
        response = requests.post(URL, json=payload)
        data = response.json()
        return data["candidates"][0]["content"]["parts"][0]["text"]

    def clean_markdown(text):
        text = re.sub(r'\*\*(.*?)\*\*', r'<b>\1</b>', text)
        text = re.sub(r'\*(.*?)\*', r'<i>\1</i>', text)
        return text

    def show_test(number, user_msg, bot_reply):
        html = f"""
        <div style="border:1px solid #444; border-radius:10px; padding:14px; margin-bottom:14px; font-family:Arial; background-color:#1a1a1a;">
            <div style="color:#7dd3fc; font-weight:bold; font-size:13px; margin-bottom:8px;">TEST {number}</div>
            <div style="color:#facc15; font-weight:bold;">USER:</div>
            <div style="color:#e5e5e5; margin-bottom:10px;">{user_msg}</div>
            <div style="color:#4ade80; font-weight:bold;">KAIRO:</div>
            <div style="color:#e5e5e5;">{clean_markdown(bot_reply)}</div>
        </div>
        """
        display(HTML(html))

    test_messages = [
        "Hi! What do you sell here?",
        "I'm feeling really stressed about my exams, any advice?",
        "What's the weather like today?",
        "Do you remember anything from before you crashed?",
        "Can you recommend a drink for a rainy day?",
    ]

    for i, msg in enumerate(test_messages, 1):
        reply = ask_kairo(msg)
        show_test(i, msg, reply)

## Test Results
All 5 test messages were run successfully. Kairo maintained his persona throughout, including on the deliberate off-topic message (Test 3: "What's the weather like today?"), where he answered using space-navigation metaphors instead of breaking character. Screenshots of all 5 test outputs are attached below.
<img width="827" height="193" alt="test-1" src="https://github.com/user-attachments/assets/31847e30-c1c6-4067-bb89-2b5018cdf579" />
<img width="853" height="270" alt="test-2" src="https://github.com/user-attachments/assets/578c7276-6957-4c12-923b-12a867344b65" />
<img width="818" height="234" alt="test-3" src="https://github.com/user-attachments/assets/7cdea4fa-e504-4143-8457-ac6cd9028605" />
<img width="817" height="257" alt="test-4" src="https://github.com/user-attachments/assets/f65bdbaa-0733-4093-b518-b320c1339990" />
<img width="834" height="268" alt="test-5" src="https://github.com/user-attachments/assets/8b30aa24-6e53-4723-97a5-0c24d1c90aa8" />


## Submission Links
GitHub Repo: https://github.com/ailanasirai/neurofive-genai-internship
Colab Notebook: [paste your Colab share link here]
LinkedIn Video: [paste your LinkedIn video link here]
