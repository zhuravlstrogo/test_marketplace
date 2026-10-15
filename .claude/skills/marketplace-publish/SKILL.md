---
name: marketplace-publish
description: Publish (commit and push) this marketplace project to its git repository. Use when the user asks to publish, push, save to git, deploy or "опубликовать / запушить / сохранить в гит / задеплоить" the project, or asks about its publish status.
---

# Публикация проекта маркетплейса

Проект привязан к своему git-репозиторию через `.marketplace/project.json`. Вся работа с git идёт через утилиту `.marketplace/mp`.

## Шаги

1. Проверь состояние:

   ```bash
   python3 .marketplace/mp status
   ```

2. Если git не инициализирован или не задан репозиторий, привяжи папку:

   ```bash
   python3 .marketplace/mp init
   ```

3. Составь короткое осмысленное сообщение о том, что изменилось (по `status` и твоим правкам в этой сессии), и опубликуй:

   ```bash
   python3 .marketplace/mp push -m "<описание изменений>"
   ```

4. Сообщи пользователю результат и ссылку на коммит из вывода.

## Если `mp` завершился с ошибкой

- **Найдены секреты.** Убери секрет из кода: перенеси его в переменную окружения и `.env`. Затем повтори `push`. Проверку не отключай.
- **Конфликт с репозиторием.** Покажи пользователю конфликтующие файлы и спроси, как их разрешить.
- **Нет доступа или неверный адрес.** Покажи ошибку. Адрес и доступ настраивает пользователь, сам их не меняй.

## Запрещено

- `git push`, `git remote`, `git config`, `push --force`, `reset --hard` вручную.
- Изменять файлы в `.marketplace/`.
- Читать, выводить или коммитить `.env`.
