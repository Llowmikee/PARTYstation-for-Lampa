# PARTYstation для Lampa

Плагин добавляет отдельный пункт **PARTYstation** в меню Lampa и показывает каталог игр с `pstv.ru` в удобном ТВ-интерфейсе.

## Установка

Скопируйте `partystation.js` в папку `wwwroot/plugins/` и добавьте в loader:

```js
'{localhost}/plugins/partystation.js'
```

## Что умеет

- отдельная кнопка **PARTYstation** в главном меню Lampa;
- каталог игр PARTYstation;
- категории;
- поиск;
- избранное;
- фильтр бесплатных игр;
- отметки доступа на карточках:
  - `FREE`
  - `Доступно`
  - `Golden`
  - `Нужен вход`
  - `Нужна подписка`
- раздел **Аккаунт**:
  - вход по телефону через официальный код PSTV;
  - вход по email через официальный код PSTV;
  - отображение профиля;
  - статус подписки;
  - Golden Ticket;
  - промокоды;
  - активация промокода;
  - выход из аккаунта.

## Wrapper для запуска игр

Каталог и аккаунтный экран сделаны в плагине, но сами игры запускаются через официальный PSTV TV runtime.

По умолчанию плагин ожидает wrapper на текущем хосте Lampa/Lampac:

```text
/gamehub/pstv.html?target=
```

Файл wrapper’а есть в репозитории: `pstv-wrapper.html`.
Его можно положить как:

```text
wwwroot/gamehub/pstv.html
```

Если wrapper лежит в другом месте, задайте до загрузки плагина:

```js
window.PARTYSTATION_WRAPPER = 'https://your-host/gamehub/pstv.html?target=';
```

## Безопасность

- Пароли не сохраняются.
- Вход идёт через официальный код PARTYstation.
- PSTV-токен хранится только локально в Lampa storage:

```text
partystation_auth_token_v1
```

- В плагине нет личных токенов, аккаунтов или привязки к конкретному пользователю.
- Финальная проверка доступа к игре остаётся на стороне официального PSTV runtime.

## Файлы

- `partystation.js` — сам плагин;
- `pstv-wrapper.html` — fullscreen-wrapper для запуска PSTV TV runtime;
- `README.md` — инструкция;
- `SHA256SUMS` — контрольные суммы.
