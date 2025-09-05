# راهنمای انتخاب سرور برای VideoTube

## 🎯 انتخاب بر اساس نیاز

### سایت شخصی/تست
- **سرور**: Oracle Cloud Free / Vultr $2.50
- **مشخصات**: 1 CPU, 1GB RAM, 20GB SSD
- **ترافیک**: تا 100 کاربر همزمان

### سایت تجاری کوچک
- **سرور**: DigitalOcean $5 / آروان کلود 60,000 تومان
- **مشخصات**: 1 CPU, 2GB RAM, 50GB SSD
- **ترافیک**: تا 500 کاربر همزمان

### سایت تجاری متوسط
- **سرور**: DigitalOcean $10 / آروان کلود 120,000 تومان
- **مشخصات**: 2 CPU, 4GB RAM, 80GB SSD
- **ترافیک**: تا 2000 کاربر همزمان

## 📋 چک‌لیست خرید سرور

### ✅ قبل از خرید بررسی کنید:
- [ ] موقعیت جغرافیایی سرور (نزدیک به کاربران)
- [ ] پشتیبانی 24/7
- [ ] امکان backup خودکار
- [ ] پنل مدیریت آسان
- [ ] امکان ارتقاء منابع
- [ ] گارانتی uptime (حداقل 99.9%)
- [ ] پشتیبانی از SSH
- [ ] فایروال و امنیت

### 💳 روش‌های پرداخت:
- **ایرانی**: کارت بانکی، درگاه پرداخت
- **خارجی**: کارت اعتباری، PayPal، Bitcoin

## 🚀 مراحل راه‌اندازی سریع

### 1. خرید سرور
```bash
# مثال برای DigitalOcean:
# 1. ثبت نام در digitalocean.com
# 2. انتخاب Droplet
# 3. انتخاب Ubuntu 22.04
# 4. انتخاب پلن $5/ماه
# 5. انتخاب منطقه (Amsterdam برای ایران)
# 6. اضافه کردن SSH Key
# 7. ایجاد Droplet
```

### 2. اتصال به سرور
```bash
# دریافت IP سرور از پنل
ssh root@YOUR_SERVER_IP

# یا با کلید SSH:
ssh -i ~/.ssh/your_key root@YOUR_SERVER_IP
```

### 3. نصب پروژه
```bash
# دانلود اسکریپت نصب
wget https://raw.githubusercontent.com/your-repo/server-commands.sh
chmod +x server-commands.sh
./server-commands.sh
```

## 🔒 تنظیمات امنیتی اولیه

```bash
# تغییر پسورد root
passwd

# ایجاد کاربر جدید
adduser videotube
usermod -aG sudo videotube

# تنظیم SSH Key
mkdir -p ~/.ssh
nano ~/.ssh/authorized_keys
# کپی کردن public key

# غیرفعال کردن ورود با پسورد
nano /etc/ssh/sshd_config
# PasswordAuthentication no
systemctl restart ssh

# تنظیم فایروال
ufw enable
ufw allow ssh
ufw allow http
ufw allow https
```

## 📊 مانیتورینگ و نگهداری

### ابزارهای مانیتورینگ:
- **htop**: مشاهده منابع سیستم
- **pm2 monit**: مانیتورینگ Node.js
- **nginx status**: وضعیت وب سرور
- **df -h**: فضای دیسک
- **free -h**: استفاده از RAM

### backup روزانه:
```bash
# اضافه کردن به crontab
crontab -e
# 0 2 * * * /home/videotube/backup.sh
```

## 🆘 پشتیبانی و عیب‌یابی

### مشکلات رایج:
1. **سایت باز نمی‌شود**: بررسی nginx و pm2
2. **کندی سایت**: بررسی RAM و CPU
3. **خطای 502**: راه‌اندازی مجدد pm2
4. **فضای دیسک تمام**: پاک کردن لاگ‌ها

### دستورات مفید:
```bash
# وضعیت سرویس‌ها
systemctl status nginx
pm2 status

# مشاهده لاگ‌ها
pm2 logs videotube
tail -f /var/log/nginx/error.log

# راه‌اندازی مجدد
pm2 restart videotube
systemctl restart nginx
```

## 📞 اطلاعات تماس پشتیبانی

### سرورهای ایرانی:
- **آروان کلود**: support@arvancloud.com
- **پارس پک**: support@parspack.com
- **ایران سرور**: support@iranserver.com

### سرورهای خارجی:
- **DigitalOcean**: Community + Documentation
- **Linode**: 24/7 Support Ticket
- **Vultr**: Support Portal