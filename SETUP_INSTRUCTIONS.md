# 🚀 ИНСТРУКЦИИ ПО ЗАВЕРШЕНИЮ НАСТРОЙКИ ПРОЕКТА

## ✅ ЧТО УЖЕ СДЕЛАНО:

1. **Gradle обновлен**: 8.6 → 8.9 ✅
2. **Устаревшие API исправлены**: lintOptions → lint, удален dexOptions ✅
3. **Пакетное имя изменено**: `org.telegram.messenger` → `com.messenger.secure` ✅
4. **Namespace обновлены** во всех модулях ✅
5. **Название приложения изменено**: "Telegram" → "Liberty" ✅
6. **Конфигурация keystore подготовлена** ✅
7. **XML файлы обновлены** (auth, contacts, shortcuts) ✅

---

## ⚠️ ЧТО НУЖНО СДЕЛАТЬ ВРУЧНУЮ:

### 1. 🔐 **СОЗДАТЬ СОБСТВЕННЫЙ KEYSTORE**

Выполните в командной строке:
```bash
cd TMessagesProj/config
keytool -genkey -v -keystore liberty.keystore -alias liberty_key -keyalg RSA -keysize 2048 -validity 10000 -storepass Liberty2024 -keypass Liberty2024 -dname "CN=Liberty, OU=Development, O=Liberty Inc, L=City, S=State, C=US"
```

### 2. 🔑 **ПОЛУЧИТЬ СОБСТВЕННЫЕ API КЛЮЧИ**

1. Перейдите на https://core.telegram.org/api/obtaining_api_id
2. Зарегистрируйте новое приложение
3. Получите `APP_ID` и `APP_HASH`
4. Замените в файле `TMessagesProj/src/main/java/org/telegram/messenger/BuildVars.java`:
   ```java
   public static int APP_ID = ВАШ_APP_ID;
   public static String APP_HASH = "ВАШ_APP_HASH";
   ```

### 3. 📱 **НАСТРОИТЬ FIREBASE**

1. Перейдите на https://console.firebase.google.com/
2. Создайте новый проект
3. Добавьте Android приложения со следующими пакетными именами:
   - `com.messenger.secure` (основное)
   - `com.messenger.secure.beta` (бета версия)
4. Включите Firebase Messaging
5. Скачайте `google-services.json` для каждого приложения
6. Замените файлы `google-services.json` в модулях:
   - `TMessagesProj/google-services.json`
   - `TMessagesProj_App/google-services.json`
   - `TMessagesProj_AppStandalone/google-services.json`
   - `TMessagesProj_AppHockeyApp/google-services.json`
   - `TMessagesProj_AppHuawei/google-services.json`

### 4. 🔧 **ОБНОВИТЬ ДОПОЛНИТЕЛЬНЫЕ КЛЮЧИ (ОПЦИОНАЛЬНО)**

В файле `BuildVars.java` также можете обновить:
```java
// Google API ключи
public static String SAFETYNET_KEY = "ВАШ_SAFETYNET_KEY";
public static String GOOGLE_AUTH_CLIENT_ID = "ВАШ_GOOGLE_CLIENT_ID";

// Huawei (если планируете поддержку)
public static String HUAWEI_APP_ID = "ВАШ_HUAWEI_APP_ID";
```

### 5. 🎨 **ЛОГОТИП УЖЕ СОЗДАН!** ✅

🕊️ **ГОТОВА ЭПИЧЕСКАЯ ИКОНКА "ГОЛУБЬ СВОБОДЫ"**
- Векторная иконка: `ic_liberty_dove.xml` ✅
- Адаптивная иконка обновлена ✅  
- Цвета добавлены ✅
- XML файлы обновлены ✅

❌ **НЕ используется** логотип Telegram 
✅ **Создан** уникальный символ свободы!

### 6. 📖 **ОПУБЛИКОВАТЬ ИСХОДНЫЙ КОД**

⚠️ **ОБЯЗАТЕЛЬНОЕ ТРЕБОВАНИЕ** лицензии GPL
- Опубликуйте свой код на GitHub/GitLab
- Укажите лицензию GPL
- Добавьте ссылку на оригинальный проект Telegram

---

## 🚀 **ГОТОВО К СБОРКЕ**

После выполнения шагов 1-3 проект будет готов к сборке:

1. Откройте Android Studio
2. Выберите File → Open → выберите папку проекта
3. Дождитесь Gradle Sync
4. Build → Make Project

---

## ⚖️ **ВАЖНЫЕ ПРАВОВЫЕ ТРЕБОВАНИЯ**

### ✅ **РАЗРЕШЕНО:**
- Использовать для разработки и тестирования
- Создавать собственные форки
- Распространять под GPL лицензией

### ❌ **ЗАПРЕЩЕНО:**
- Использовать название "Telegram"
- Использовать логотип Telegram
- Использовать пакет `org.telegram.messenger`
- Скрывать исходный код (GPL требует публикации)

### 📋 **ОБЯЗАТЕЛЬНО:**
- Уведомлять пользователей что это неофициальная версия
- Публиковать исходный код
- Соблюдать требования безопасности

---

## 🆘 **ПОДДЕРЖКА**

- **Документация Telegram API**: https://core.telegram.org/api
- **MTProto протокол**: https://core.telegram.org/mtproto
- **Безопасность**: https://core.telegram.org/mtproto/security_guidelines
- **Воспроизводимые сборки**: https://core.telegram.org/reproducible-builds

---

**⚡ ПРОЕКТ ГОТОВ К ЗАПУСКУ! Технические проблемы Gradle решены.** 