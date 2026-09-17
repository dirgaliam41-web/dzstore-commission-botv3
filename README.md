# DZS Commission Bot — V7.2

Bot commission Discord dengan panel terpisah untuk setiap jenis commission.

## Setup command

Gunakan masing-masing command di channel tempat panel ingin dipasang:

- `/setup-commission skin`
- `/setup-commission render`
- `/setup-commission logo`
- `/setup-commission animasi`

Setiap item punya panel dan tombol order sendiri. Panel yang sama akan diperbarui jika command setup untuk item tersebut dijalankan lagi di channel yang sama.

## Alur order

1. Customer klik panel item.
2. SKIN memilih ukuran 64 / 128 / 256 / 512.
3. Customer mengisi detail request.
4. Bot membuat private ticket dengan Order ID `DZS-0001`, `DZS-0002`, dst.
5. Worker wajib **Claim**.
6. Setelah Claim, status otomatis menjadi **Progress**.
7. Worker dapat mengubah status menjadi Waiting atau Progress.
8. Worker/Admin menyelesaikan order dengan **Completed** / **Close Ticket**.
9. Customer memilih rating 1–5 dan menulis review.
10. Feedback dikirim ke channel feedback dengan profil Worker.
11. Setelah feedback berhasil dikirim, ticket dihapus otomatis **15 detik kemudian**.

## Proteksi

- 1 user hanya boleh mempunyai 1 ticket aktif.
- Ticket tidak bisa Completed sebelum di-Claim.
- Hanya Worker yang Claim atau Admin yang dapat menyelesaikan ticket.
- Feedback hanya dapat dikirim oleh customer pemilik order.
- Feedback tidak dapat dikirim dua kali untuk order yang sama.
- Tidak membutuhkan Privileged Gateway Intents.
- Cleanup otomatis tetap tersedia sebagai pengaman untuk ticket completed lama.

## Railway Variables

```env
DISCORD_TOKEN=PASTE_BOT_TOKEN_HERE
GUILD_ID=PASTE_SERVER_ID_HERE
TICKET_CATEGORY_ID=PASTE_TICKET_CATEGORY_ID_HERE
FEEDBACK_CHANNEL_ID=PASTE_FEEDBACK_CHANNEL_ID_HERE
LOG_CHANNEL_ID=PASTE_LOG_CHANNEL_ID_HERE
STAFF_ROLE_ID=PASTE_STAFF_ROLE_ID_HERE
```

Bot membutuhkan permission minimal untuk membuat/mengelola ticket, termasuk **Manage Channels**, serta permission membaca dan mengirim pesan di channel terkait.


### Skin size selector
Panel `/setup-commission skin` uses a Discord dropdown like a ticket selector with 64×64, 128×128, 256×256, and 512×512 options. Selecting a size opens the order modal directly.
