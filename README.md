const userMap = {
　"中島亜星": "979005564103311380",
  　"あせい": "979005564103311380",
  "校舎長": "979005564103311380",
  "塚越稀介": "829881129859153941",  
   "きすけ": "829881129859153941",
　"明石陽生": "684378404925079593",
  "ようせい": "684378404925079593",
  "山瀬壮飛": "1217395961006129214",
  "たけと": "1217395961006129214",
  "小林理乃": "1217823122720424037",
  "りの": "1217823122720424037",
  "中澤龍之介": "1221688583920947240",
  "りゅうのすけ": "1221688583920947240",
  "吉永みのり": "1217843336203866232",
    "みのり": "1217843336203866232",
  "大菅珠月": "1073530006552199180",
   "みつき": "1073530006552199180",
  "砂本真奈": "1351890920445837425",
  "まな": "1351890920445837425",
  "窪田彩乃": "1348571564265705492",
   "あやの": "1348571564265705492",
　"木村連": "1348571564265705492",
  "れん": "1348571564265705492",
  "西山蓮人": "1217476279402762353",
  "れんと": "1217476279402762353",
  "谷田映月": "1217736498783191090",
  "はづき": "1217736498783191090",
  "鈴木麻央": "1349661977089413233",
  "まお": "1349661977089413233",
  "高橋昇吾": "1351181909308473448",
   "しょうご": "1351181909308473448",
  "今泉賢人": "1348571564265705492",
   "けんと": "1348571564265705492",
  "小幡魁河": "1221690449710944359",
  "かいが": "1221690449710944359",
  "鈴木俊貴": "631508357705891861",
  "としき": "631508357705891861",
 "えりか": "1484454122576150532",
  "エリカ": "1484454122576150532",
"川神エリカ": "1484454122576150532",
"近藤紬希": "1479694922939633766",
  "つむぎ": "1479694922939633766",
"古澤空希": "1485461270416330916",
"そらき": "1485461270416330916",
  "中里凛々香": "1356558060960747570",
  "りりか": "1356558060960747570",
  
}


// ===== 生徒パスワードリスト =====
const studentPasswords = [
  "b34P","Fy3d","ur6w","efC5","5gZv","rFi7","SLJ4","t4Tv","t3rw","hi9q","hm5A","ji3f","f3ZU","9DHw","5Lcf","4YyN",
  "d2VA","bE8n","F7KA","G5Vu","7p7T","C4kP","t6qH","J9QH","LEg2","w4ns","uH2g","KY6f","8r4V","Xb3m","L9ae","e36f",
  "4pwn","dbk4","9wV2","D6m6","uAz3","E2Yg","L5db","f4Ym","emZ5","PVw4","JjR4","KT6A","R9fy","Gjq3","dhd5","sw5t",
  "n8Ns","QF9h","8B35","RDK4","x2Uc","3KsF","z5AK","kk4t","3r4s","du8G","jPU3","6phQ","MW7G","t29b","6wiS","UXQ5",
  "syP7","3JeZ","hQY5","G3eh","Nzz5","8XwK","NHQ6","YXH6","W9AU","Uxd5","5gW9","XN6T","aM48","LsB6","j6Vg","WKH3",
  "Gdp8","9s4Z","7duu","VL7s","5r5i","YkJ7","6UvT","G5zi","6qEq","4WTJ","bZ6S","8QN6","b8wc","HPB4","yn6w","rq2E",
  "jTm9","6fJh","tvk7","6p5K","ej3f","q2Ap","Y8Pn","NTY3","x6m2","yUv5","Ane3","j8iX","G5AP","tPA7","C4nk","CT9y",
  "y7WJ","U27u","pHE8","J9Zv","6hRx","gMW9","B9zx","V2sK","xr54","SD5J","rk4D","CJ5T","rc7Z","DnD5","Qrt9","UKs2",
  "8sBm","z6Mi","gf2r","UH9x","Gxi8","yfd8","Q9xa","Ta7n","CE8K","AKk9","Hec5","pk6b","m9Pt","7Wzf","Xww7","L3yj",
  "Hp8T","Z4xd","4xee","rFG6","NAL5","T7Vu","JP48","huu6","wL4E","vp6K","tPg4","sc2T","SF7S","GCD2","i7mb","eQy7",
  "bA9L","sms5","ej5j","i6ej","LU4a","8LLq","A2rB","b7sV","nU4L","sa7P","4TXu","aXC8","L8iN","bWH3","aq8W","Vv4u",
  "Hj9L","jn4U","yee4","Y8Gv","T4Db","F7gT","4a3V","MZ7r","y6AW","3DBk","xK83","DTi6","XaL8","mpm5","dFk9","SiU7",
  "5KhG","cEg4","ZAZ4","N5BR","rX5Z","yV3d","KR6R","jLX5","1433m"
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
