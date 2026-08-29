# Burmalgram

Burmalgram — минималистичный web-мессенджер на Firebase, стилистически вдохновлённый Telegram/Discord.

## Что исправлено в этой версии

- Убрана зависимость от Firebase Storage: нет загрузки фото, файлов и аватаров.
- Профиль теперь открывается кликом по своей панели и позволяет менять имя, username и описание.
- Настройки приложения работают: профиль, конфиденциальность, уведомления, тема, анимации, список блокировок, выход.
- Группы и каналы создаются через Firestore, с обработкой ошибок и добавлением участников в группу.
- Личные чаты работают через Firestore Realtime listeners.
- Каналы позволяют писать только владельцу/администратору.
- Интерфейс сделан ближе к Telegram: узкая левая панель, большой список диалогов, верхняя панель чата, отдельное меню настроек.
- Вложения отключены до подключения Firebase Storage.

## Firebase

Проект: `burmalgram-91a54`.

Нужно включить:

1. Authentication → Email/Password
2. Authentication → Google
3. Firestore Database
4. Authentication → Settings → Authorized domains — добавить домен GitHub Pages и `localhost`, если тестируете локально.

Storage не нужен для текущей версии.

## GitHub Pages

Загрузите содержимое папки проекта в корень репозитория. Затем:

Settings → Pages → Deploy from a branch → `main` → `/ (root)`.

После публикации обязательно добавьте домен GitHub Pages в Firebase Authorized domains.

## Локальный запуск

Откройте папку проекта через VS Code + Live Server или выполните:

```bash
python -m http.server 5500
```

и откройте `http://localhost:5500`.
