# CMS Integration Notes (Welcome Bonus LP)

## Быстрый чеклист перед отправкой в CMS

1. Модалки:
- Не использовать `:target` + `href="#..."`.
- Использовать `input[type="checkbox"]` + `label for="..."` + `:has(...)`.

2. Скрытые переключатели:
- Добавить 5 инпутов:
  - `modal-info-toggle`
  - `modal-first-toggle`
  - `modal-second-toggle`
  - `modal-third-toggle`
  - `modal-fourth-toggle`

3. Открытие/закрытие модалок:
- Иконки info: `label` с `for="modal-...-toggle"`.
- Кнопка закрытия `×`: тоже `label for="modal-...-toggle"`.
- Backdrop: `label for="modal-...-toggle"` (не `a href="#"`).

4. Ссылки:
- Кнопки Deposit: `href="/deposit"`.
- T&C: `href="/terms-and-conditions"`.
- Не оставлять `href="#"`.

5. CSS для модалок:
- `z-index: 9999`.
- Фон оверлея + блюр:
  - `background: rgba(1, 6, 30, 0.6)`
  - `backdrop-filter: blur(24px)`
- Показ модалок только через `:has(#modal-...:checked)`.
- Блокировка скролла `body` через `body:has(#modal-...:checked) { overflow: hidden; }`.

6. Ассеты (если требует CMS):
- Использовать absolute URL вида `https://nightwin.com/content/uploads/...`.
- Обычно это минимум:
  - `info.png`
  - `chevron_up.png`
  - баннеры/уголки (если клиент просит хостить в CMS).

7. Мелочи по верстке:
- `body { overflow-x: hidden; }`.
- Для контейнера:
  - `width: 100%`
  - `position: relative`
- Для скрытых инпутов:
  - `left: 0; top: 0;`

## Мини-шаблон структуры модалки (CMS)

```html
<input class="nw-hidden-input" type="checkbox" id="modal-info-toggle">

<label class="wb-info-trigger" for="modal-info-toggle" aria-label="Open bonus details">
  <img src="https://nightwin.com/content/uploads/info.png" alt="Info">
</label>

<section class="wb-modal" id="bonus-details" aria-label="Bonus Details">
  <label class="wb-modal-backdrop" for="modal-info-toggle" aria-label="Close popup"></label>
  <div class="wb-modal-dialog">
    <div class="wb-modal-head">
      <h3>Bonus Details</h3>
      <label class="wb-modal-close" for="modal-info-toggle" aria-label="Close popup">×</label>
    </div>
    <div class="wb-modal-content">
      ...
    </div>
  </div>
</section>
```

## Проверка перед релизом

1. Все модалки открываются и закрываются по иконке, крестику и фону.
2. При открытой модалке фон не скроллится.
3. Нет `href="#"`.
4. Ссылки ведут на `/deposit` и `/terms-and-conditions`.
5. Контент офферов/FAQ не изменен случайно при CMS-правках.
