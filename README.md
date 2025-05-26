import json
import urllib.request
import urllib.error

webhook_url = "https://discord.com/api/webhooks/1376425995099181208/laTTIQaY4yGaQOaNk8O4wJBs1emYVKQh4DNZ4jYBJxir4emmKUbIJqtX0_jxGsk3F5cW"  # ← Thay đúng URL mới

data = {
    "content": "✅ Webhook hoạt động rồi nè!"
}

headers = {
    "Content-Type": "application/json"
}

req = urllib.request.Request(
    url=webhook_url,
    data=json.dumps(data).encode('utf-8'),
    headers=headers,
    method='POST'
)

try:
    with urllib.request.urlopen(req) as response:
        print("✅ Thành công! Mã phản hồi:", response.status)
except urllib.error.HTTPError as e:
    print("❌ HTTP Error:", e.code, e.reason)
    print("📩 Phản hồi từ Discord:", e.read().decode())
except urllib.error.URLError as e:
    print("❌ URL Error:", e.reason)

