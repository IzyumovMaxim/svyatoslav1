# ВолгаНефтеСтрой

Сайт ООО «ВолгаНефтеСтрой» — Vue 3 + Vite + Tailwind CSS.

## Локальный запуск

```bash
npm install
npm run dev
```

## Сборка

```bash
npm run build
```

## GitHub Pages

Сайт публикуется автоматически при push в `main`.

URL: https://izyumovmaxim.github.io/svyatoslav1/

## Форма «Перезвоните мне»

Заявки отправляются через [Web3Forms](https://web3forms.com) на почту владельца ключа.
Зарегистрируйтесь там на нужную почту и вставьте Access Key в `formAccessKey` в `src/data/site.ts`.
Пока ключа нет, форма показывает «Не удалось отправить заявку» и номер телефона.

## Логотипы партнёров

Файлы кладутся в `public/img/partners/` (`transneft.svg`, `magma.svg`, `tagras.svg`), список — массив
`partners` в `src/data/site.ts`. Пока файла нет, вместо логотипа выводится название компании.
