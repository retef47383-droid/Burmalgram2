# Burmalgram

Burmalgram — минималистичный web-мессенджер на Firebase.

## Что уже работает

- регистрация и вход по email/password;
- вход через Google (после включения Google provider в Firebase Authentication);
- профиль, юзернейм, bio и загрузка аватара через Firebase Storage;
- поиск пользователей по `@username` или email;
- личные чаты в реальном времени;
- создание групп и каналов;
- realtime-сообщения через Cloud Firestore;
- базовые настройки конфиденциальности;
- блокировка/разблокировка пользователей;
- настройки уведомлений в localStorage;
- адаптивный интерфейс для компьютера и телефона;
- PWA manifest.

## Важно: один раз настроить Firebase

Файл уже настроен на проект `burmalgram-91a54`: из предоставленного Google/Firebase JSON взяты project ID, Storage bucket, project number и API key. Сам JSON содержит Android-клиент (`com.burmalgram.app`), а web-клиент Firebase должен быть зарегистрирован отдельно в Console; поэтому я намеренно не подставлял выдуманный web `appId`.

В Firebase Console для проекта включите:

1. **Authentication → Sign-in method → Email/Password**.
2. **Authentication → Sign-in method → Google**.
3. **Firestore Database** в production mode.
4. **Storage**.
5. **Project settings → Your apps → Web app**: зарегистрируйте web-приложение и при необходимости добавьте настоящий web config в `index.html` (особенно `appId`).
6. Добавьте домен, где будет опубликован сайт, в **Authentication → Settings → Authorized domains**.

Для GitHub Pages добавьте, например, `YOURNAME.github.io` и домен репозитория/сайта, который покажет GitHub.

## Локальный запуск

Простое открытие `index.html` показывает интерфейс, но Google/Firebase Authentication надёжнее тестировать через локальный web-сервер.

В VS Code удобно установить Live Server и открыть `index.html` через **Open with Live Server**.

Либо из папки проекта:

```bash
python -m http.server 5500
```

После этого откройте `http://localhost:5500`.

## GitHub Pages

1. Создайте репозиторий.
2. Загрузите содержимое этой папки.
3. В GitHub откройте **Settings → Pages**.
4. В качестве источника выберите ветку `main` и корень `/ (root)`.
5. После публикации добавьте GitHub Pages домен в Firebase Authorized domains.

## Правила

`firestore.rules` и `storage.rules` — стартовые правила безопасности. Перед публичным запуском их стоит дополнительно проверить под вашу модель ролей, модерирования и приватности.

## Примечание про "полностью рабочий Telegram"

Это готовое ядро web-мессенджера, а не полный клон Telegram со всеми серверными микросервисами. В UI уже заложены основные сценарии. Для промышленной версии обычно отдельно добавляют push-уведомления, медиа-сообщения, голос/видео, поиск по индексу, модерацию, rate limits, полноценные роли каналов/групп и серверную обработку.
