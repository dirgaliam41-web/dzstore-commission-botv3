# DZS Commission Bot V7.1 — Full Automatic Workflow

Discord commission ticket bot untuk Railway / Render / Pterodactyl.

## Fitur utama
- Panel Commission tersimpan dan bisa diperbarui tanpa membuat panel baru berulang kali.
- 1 user = 1 ticket aktif.
- Nomor order otomatis DZS-0001, DZS-0002, dst.
- 4 jenis commission: Skin (64/128/512), Render, Logo, Animasi.
- Worker wajib Claim sebelum ticket bisa Completed.
- Saat Worker Claim, status otomatis berubah dari Open -> Progress.
- Worker yang sudah Claim menjadi pemilik ticket; Worker lain tidak dapat merebutnya.
- Alur otomatis: Open -> Claim/Progress -> Waiting (bila perlu) -> Completed -> Rating/Feedback -> ticket dihapus.
- Completed dari tombol maupun `/order-status completed` masuk ke alur feedback otomatis.
- Setelah feedback disimpan, ticket langsung dihapus tanpa admin.
- Jika feedback tidak diberikan, ticket Completed otomatis dihapus setelah 24 jam.
- Bot menjalankan cleanup berkala setiap 10 menit dan cleanup awal setelah startup.
- Feedback menampilkan Worker, avatar/profile Discord Worker, Reviewer, Rating, Ulasan, Order, dan Commission.
- SQLite database.
- Discord intents hanya `Guilds`, sehingga tidak membutuhkan Privileged Gateway Intents.

## Environment Variables
```env
DISCORD_TOKEN=PASTE_BOT_TOKEN_HERE
GUILD_ID=PASTE_SERVER_ID_HERE
TICKET_CATEGORY_ID=PASTE_TICKET_CATEGORY_ID_HERE
FEEDBACK_CHANNEL_ID=PASTE_FEEDBACK_CHANNEL_ID_HERE
LOG_CHANNEL_ID=PASTE_LOG_CHANNEL_ID_HERE
STAFF_ROLE_ID=PASTE_STAFF_ROLE_ID_HERE
```

## Deploy Railway
1. Upload source ke GitHub.
2. Railway -> New Project -> Deploy from GitHub Repo.
3. Isi Variables di atas.
4. Deploy.
5. Pastikan log menunjukkan `LOGIN BERHASIL` dan `COMMANDS REGISTERED KE SERVER`.
6. Di Discord jalankan `/setup-commission` satu kali pada channel commission.

## Flow Worker
1. Customer membuat ticket.
2. Worker klik **Claim**.
3. Bot otomatis mengubah status menjadi **Progress**.
4. Worker dapat memakai **Waiting** bila membutuhkan jawaban/customer.
5. Setelah pekerjaan selesai, Worker klik **Completed**.
6. Bot meminta customer memberi rating.
7. Customer mengirim ulasan.
8. Feedback diposting ke channel feedback dengan profil Worker.
9. Ticket langsung dihapus.

## Catatan
- Jika customer tidak memberi feedback, ticket Completed dibersihkan otomatis setelah 24 jam.
- Admin tetap bisa mengambil alih penyelesaian ticket.
- Bot membutuhkan permission Manage Channels untuk membuat dan menghapus ticket.
