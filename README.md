# ai-agent-gemini
AI Agent built using Python and Google Gemini API that answers civil engineering queries via HTTP endpoint.
flask
google-generativeai
gunicorn

from flask import Flask, request, jsonify
import google.generativeai as genai

app = Flask(__name__)

genai.configure(api_key="YOUR_API_KEY")

model = genai.GenerativeModel("gemini-pro")

@app.route("/", methods=["GET"])
def home():
    return "AI Agent Running"

@app.route("/ask", methods=["POST"])
def ask():
    data = request.json
    question = data.get("question")

    response = model.generate_content(question)

    return jsonify({"answer": response.text})

if __name__ == "__main__":
    app.run()
