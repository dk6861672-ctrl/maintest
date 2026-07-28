// /api/chat.js
// Vercel serverless function — keeps the Gemini API key on the server.
// Reads the key from the Vercel Environment Variable "GEMINI_API_KEY".
// Never expose this key in front-end code.

export default async function handler(req, res) {
  if (req.method !== "POST") {
    return res.status(405).json({ error: "Method not allowed" });
  }

  const apiKey = process.env.GEMINI_API_KEY;
  if (!apiKey) {
    return res.status(500).json({ error: "Server is missing GEMINI_API_KEY" });
  }

  const { contents } = req.body || {};
  if (!Array.isArray(contents)) {
    return res.status(400).json({ error: "Request body must include a 'contents' array" });
  }

  const GEMINI_MODEL = "gemini-2.0-flash";
  const GEMINI_URL = `https://generativelanguage.googleapis.com/v1beta/models/${GEMINI_MODEL}:generateContent?key=${apiKey}`;

  try {
    const geminiRes = await fetch(GEMINI_URL, {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({
        contents,
        systemInstruction: {
          parts: [
            {
              text: "You are Krixel AI, a friendly doubt-solving assistant for students preparing for CUET-UG and general aptitude exams (English, GK, Mental Ability, Science). Keep answers clear, concise, and exam-focused.",
            },
          ],
        },
      }),
    });

    const data = await geminiRes.json();

    if (!geminiRes.ok) {
      return res.status(geminiRes.status).json({ error: data?.error?.message || "Gemini API error" });
    }

    const reply =
      data?.candidates?.[0]?.content?.parts?.[0]?.text ||
      "Sorry, I couldn't generate a response. Please try again.";

    return res.status(200).json({ reply });
  } catch (err) {
    console.error("Gemini proxy error:", err);
    return res.status(500).json({ error: "Failed to reach Gemini API" });
  }
}
