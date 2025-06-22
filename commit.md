# 📘 Conventional Commit Guide

## 🔧 انواع `type`‌های رایج

| Type       | توضیح                                                                 |
|------------|----------------------------------------------------------------------|
| `feat`     | اضافه کردن یک قابلیت جدید                                           |
| `fix`      | رفع باگ                                                              |
| `docs`     | تغییرات مربوط به مستندات (مثل README یا توضیحات کد)                |
| `style`    | تغییرات ظاهری فقط (مثل فاصله، سمی‌کالن و ...)                      |
| `refactor` | بازنویسی کد بدون تغییر در رفتار آن                                  |
| `test`     | اضافه یا تغییر تست‌ها                                               |
| `chore`    | تغییراتی غیر از فیچر و باگ (مثل تغییر در پکیج‌ها یا اسکریپت‌ها)   |
| `perf`     | بهبود عملکرد                                                         |
| `ci`       | تغییرات مرتبط با CI/CD                                              |
| `build`    | تغییرات مربوط به build system یا پکیج منیجر (مثل webpack یا yarn)  |

---

## 🎯 چند مثال خوب از کامیت

```bash
feat(auth): add JWT token generation

fix(pets): handle crash when pet image is missing

docs(readme): update usage instructions

style: format form inputs and fix indentation

refactor(pets): separate pet card into its own component

test(login): add test case for incorrect credentials

chore: update dependencies to latest versions

perf(image): lazy-load images for better performance
