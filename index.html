<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>Discord メンション通知フォーム</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 40px;
      background-color: #f9f9f9;
      color: #333;
    }
    h1 {
      text-align: center;
      color: #5865F2;
    }
    form {
      max-width: 500px;
      margin: 0 auto;
      background: #fff;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }
    label {
      font-weight: bold;
    }
    input, textarea {
      width: 100%;
      padding: 8px 10px;
      margin: 6px 0 12px 0;
      border: 1px solid #ccc;
      border-radius: 6px;
      box-sizing: border-box;
    }
    button {
      background-color: #5865F2;
      color: white;
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-size: 16px;
      width: 100%;
    }
    button:hover {
      background-color: #4752C4;
    }
    #status {
      text-align: center;
      margin-top: 20px;
      font-weight: bold;
    }
    #status.success {
      color: green;
    }
    #status.error {
      color: red;
    }
    #sentMessages {
      max-width: 500px;
      margin: 20px auto 0;
      padding: 10px;
      background: #fff;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.05);
    }
    #sentMessages h2 {
      font-size: 18px;
      margin-bottom: 10px;
    }
    #sentMessages ul {
      list-style: none;
      padding-left: 0;
    }
    #sentMessages li {
      padding: 4px 0;
      border-bottom: 1px solid #eee;
    }
  </style>
</head>
<body>
  <h1>Discord メンション通知フォーム</h1>

  <form id="form">
    <label>先生の名前:</label>
    <input type="text" id="userName"　placeholder="例: 校舎長">

    <label>メッセージ（内容はすべての先生が見ることができます）:</label>
    <textarea id="message" rows="4" required></textarea>

    <label>パスワード:</label>
    <input type="password" id="password" required />

    <label>生徒の名前:</label>
    <input type="text" id="discordId" required />

    <button type="submit">送信</button>
  </form>

  <div id="status"></div>

  <div id="sentMessages">
    <h2>送信済みメッセージ</h2>
    <ul id="messagesList"></ul>
  </div>

  <script>
    const form = document.getElementById('form');
    const statusEl = document.getElementById('status');
    const messagesList = document.getElementById('messagesList');

    form.addEventListener('submit', async (e) => {
      e.preventDefault();

      const userName = document.getElementById('userName').value.trim();
      const message = document.getElementById('message').value.trim();
      const password = document.getElementById('password').value.trim();
      const discordId = document.getElementById('discordId').value.trim();

      if (!userName || !message || !password) {
        statusEl.textContent = '名前・メッセージ・パスワードは必須です';
        statusEl.className = 'error';
        return;
      }

      if (!discordId) {
        statusEl.textContent = 'Discord IDは必須です（名前がuserMapにない場合）';
        statusEl.className = 'error';
        return;
      }

      statusEl.textContent = '送信中…';
      statusEl.className = '';

      try {
        const res = await fetch('/api/send', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({ userName, message, password, discordId })
        });

        const data = await res.json();

        if (data.success) {
          statusEl.textContent = `✅ ${userName} さんの送信成功！`;
          statusEl.className = 'success';
          form.reset();

          // 送信済みメッセージに追加
          const li = document.createElement('li');
          li.textContent = `${userName}: ${message}`;
          messagesList.appendChild(li);

        } else {
          statusEl.textContent = '❌ エラー: ' + (data.error || '不明');
          statusEl.className = 'error';
        }
      } catch (err) {
        statusEl.textContent = '❌ サーバーエラー: ' + err.message;
        statusEl.className = 'error';
      }
    });
  </script>
</body>
</html>
