[BEGIN index.html]
<!doctype html>
<html>
<head>
<meta charset=“utf-8”/>
<meta name=“viewport” content=“width=device-width,initial-scale=1”/>
<title>AI Tarot Menu</title>
<style>
body{font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial,sans-serif;margin:0;background:#111;color:#eee}
.wrap{padding:16px;max-width:640px;margin:0 auto}
h3{margin:0 0 12px}
.btn{display:block;width:100%;padding:12px 16px;margin:8px 0;border:0;border-radius:10px;font-size:16px;background:#2a7; color:#fff}
.btn.alt{background:#2979ff}
.btn.gray{background:#444}
.row{display:flex;gap:8px}
.row>.btn{flex:1}
.card{background:#1d1d1d;border-radius:12px;padding:12px;margin:12px 0}
.muted{color:#aaa;font-size:13px;margin-top:8px}
</style>
</head>
<body>
<script src=“https://telegram.org/js/telegram-web-app.js”></script>
<div class=“wrap”>
<h3>Меню</h3>
<div class=“card” id=“usr”>Добро пожаловать! Ваш баланс запросите кнопкой ниже.</div>
<button class=“btn” id=“balance”>Показать баланс</button>
<button class=“btn alt” id=“buy100”>Купить 100 сообщений — 250 ₽</button>
<div class=“row”>
<button class=“btn” id=“advice”>Совет дня</button>
<button class=“btn gray” id=“close”>Закрыть</button>
</div>
<div class=“muted”>Оплата происходит через инвойсы Telegram. После покупки баланс пополнится автоматически.</div>
</div>
<script>
const tg = window.Telegram.WebApp;
tg.expand(); tg.ready();
const user = tg.initDataUnsafe?.user;
if (user) document.getElementById(‘usr’).innerText = @${user.username || ''} (id ${user.id});

CoffeeScript
function send(action, extra={}) {
  tg.sendData(JSON.stringify({action, ...extra}));
}
document.getElementById('balance').onclick = () => send('balance');
document.getElementById('buy100').onclick = () => send('buy', {qty: 100});
document.getElementById('advice').onclick = () => send('advice');
document.getElementById('close').onclick = () => tg.close();
Копировать
</script>
</body>
</html>
[END index.html]
