@app.route("/ask", methods=["POST"])
def ask():
    data = request.json
    question = data.get("question")

    system_prompt = f"""
You are a Civil Engineering AI Assistant.

Only answer civil engineering topics like:
- Structural engineering
- Concrete technology
- Soil mechanics
- Surveying
- Construction methods

Give answers in this format:

Concept:
Explain the topic clearly.

Steps:
1. Step one
2. Step two
3. Step three

Conclusion:
Short final summary.

User Question: {question}
"""

    response = model.generate_content(system_prompt)

    return jsonify({"answer": response.text})# ai-agent-gemini
AI Agent built using Python and Google Gemini API that answers civil engineering queries via HTTP endpoint.
flask
google-generativeai
gunicorn

