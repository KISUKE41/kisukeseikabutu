const userMap = {
　"人": "数字",
  
}


// ===== 生徒パスワードリスト =====
const studentPasswords = [
  "password",
];


// ===== Discord Webhook URL =====
const webhookUrl = "https://discordapp.com/api/webhooks/1432296431401566258/Bq0Kx7izcPRHHsqnHO1Qe62pqw418twYt_MTI31yZd3Sskj-WIqQlj9PP4Xi2u2HUTCt";

export default async function handler(req, res) {
  if (req.method !== 'POST') return res.status(405).json({ error: 'POSTのみ対応' });

  try {
    const { userName, message, password, discordId } = req.body;

    if (!userName || !message || !password || !discordId) {
      return res.status(400).json({ error: 'userName, message, password, discordId は必須です' });
    }

    // パスワードチェック
    if (!studentPasswords.includes(password)) {
      return res.status(403).json({ error: '無効なパスワードです' });
    }

    // 名前 → Discord ID 変換、または入力IDをそのまま使用
    const finalDiscordId = userMap[userName] || discordId;

    const payload = {
      content: `<@${finalDiscordId}> ${discordId}がよんでます！\n　${message}\n🔑 パスワード: ${password}`,
      allowed_mentions: { users: [finalDiscordId] }
    };

    const discordRes = await fetch(webhookUrl, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(payload)
    });

    if (!discordRes.ok) {
      const discordError = await discordRes.text();
      return res.status(500).json({ error: 'Discord送信失敗', details: discordError });
    }

    return res.status(200).json({ success: true });

  } catch (err) {
    return res.status(500).json({ error: 'サーバーエラー', details: err.message });
  }
}
