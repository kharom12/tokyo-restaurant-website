# 🚀 Deploy Guide — Tokyo Express Website

## ⚠️ Nếu bạn đã push và Railway build fail

Đó là vì repo `kharom12/tokyo-restaurant-website` còn nội dung cũ. Làm theo bước bên dưới để **ghi đè**.

---

## Bước 1 — Force push ghi đè repo cũ (trên Terminal Mac)

Mở Terminal và chạy:

### 1a. Đi vào folder

Kéo thẳng folder **"Website Restaurant"** vào Terminal sau khi gõ `cd `, ví dụ:

```bash
cd "/Users/<tên bạn>/.../Website Restaurant"
```

### 1b. Xóa .git cũ (nếu có) và init sạch

```bash
rm -rf .git
git init -b main
git config user.email "kha@bukkii.ai"
git config user.name "Kha"
```

### 1c. Stage & commit

```bash
git add .
git commit -m "Tokyo Express restaurant website"
```

### 1d. Kết nối với repo GitHub và force-push

```bash
git remote add origin https://github.com/kharom12/tokyo-restaurant-website.git
git branch -M main
git push -u origin main --force
```

> ⚠️ `--force` sẽ **xóa sạch** nội dung cũ trên GitHub (backend/, frontend/, deploy.sh...)
> và thay bằng code Tokyo Express. Chỉ dùng nếu bạn chắc chắn repo cũ không cần nữa.

> 💡 Nếu Git hỏi password: dùng **Personal Access Token** thay password.
> Tạo tại https://github.com/settings/tokens/new — chọn scope `repo`.

---

## Bước 2 — Verify trên GitHub

Mở https://github.com/kharom12/tokyo-restaurant-website — bạn phải thấy:

```
├── images/             (24 ảnh)
├── .gitignore
├── DEPLOY.md
├── README.md
├── index.html
├── package.json
└── railway.json
```

Nếu **KHÔNG** thấy đúng các file này → push chưa thành công, chạy lại bước 1.

---

## Bước 3 — Railway redeploy

Sau khi code đúng đã lên GitHub:

1. Vào Railway project.
2. Click **Redeploy** (hoặc Railway sẽ tự detect commit mới và deploy lại).
3. Build sẽ chạy Railpack → nhận ra `package.json` có Node → cài `serve` → chạy `npm start`.
4. Sau ~1–2 phút: **Deployed** ✅
5. Settings → Networking → **Generate Domain** để lấy URL.

---

## Update sau này

Mỗi lần sửa website:

```bash
git add .
git commit -m "mô tả thay đổi"
git push
```

Railway tự redeploy trong ~1 phút.

---

## Troubleshooting Railway

| Lỗi | Fix |
|---|---|
| `Script start.sh not found` + liệt kê Node/Python... | Repo không có `package.json` → push lại đúng folder |
| `Module 'serve' not found` | Railway chưa npm install được → check `package.json` có `serve` trong dependencies |
| Build thành công nhưng deploy crash | Check Deploy Logs, thường do `$PORT` env → `package.json` đã config đúng rồi |
| Website hiện 404 | Check domain URL, thử force redeploy |
