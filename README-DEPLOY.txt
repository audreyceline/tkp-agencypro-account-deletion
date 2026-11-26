TKP AgencyPro - Vercel Deployment

Isi ZIP ini adalah isi folder deployment yang harus ditempatkan langsung di ROOT repository Vercel.

Isi:
- index.html
- verify-email/
- delete-account/
- reset-password/
- icons/
- favicon.png
- manifest.json

Route Reset Password:
https://www.tkpagencypro.com/reset-password

PENTING:
1. Pertahankan seluruh route lama. Jangan menghapus verify-email/ atau delete-account/.
2. Pada Supabase Dashboard > Authentication > URL Configuration, tambahkan URL berikut ke Redirect URLs:
   https://www.tkpagencypro.com/reset-password
   Jangan hapus redirect URL lama yang masih digunakan.
3. Pada Authentication > Email Templates > Reset Password, gunakan tautan yang mengarah ke {{ .RedirectTo }} dan membawa token_hash, dengan type=recovery. Contoh:
   <a href="{{ .RedirectTo }}?token_hash={{ .TokenHash }}&type=recovery">Atur ulang password</a>
   Pastikan template Reset Password saja yang diubah. JANGAN mengubah Confirm signup, karena alur OTP pendaftaran yang sudah berjalan harus tetap dipertahankan.
4. Resend digunakan sebagai SMTP provider yang dikonfigurasi di Supabase Auth. Halaman ini tidak menyimpan API key Resend.
5. Setelah upload isi ZIP ini ke root repository Vercel dan deployment selesai, uji URL:
   https://www.tkpagencypro.com/reset-password
6. Uji alur dari aplikasi: Login > Lupa password > masukkan email > buka email recovery > atur password baru > login kembali.

Project Supabase:
https://iggqlasoxkaiybcnkrmb.supabase.co

Kunci publishable yang digunakan di halaman web adalah kunci publik (publishable), bukan service_role.
Jangan pernah menaruh service_role key atau API key rahasia Resend di file publik.
