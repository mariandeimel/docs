---
layout: ~/layouts/MainLayout.astro
title: Структура проекта
description: Изучите структуру Astro проекта.
i18nReady: true
---

Ваш новый проект Astro, созданный с помощью `create-astro`, уже включает в себя некоторые файлы и папки.
Другие вы создадите сами и добавите в существующую файловую структуру Astro.

Вот как организован проект Astro, и некоторые файлы, которые вы найдете в своем новом проекте.

## Директории и Файлы

В корне проекта Astro должны находится следующие каталоги и файлы:

- `src/*` - Исходный код вашего проекта (компоненты, страницы, стили, и т.д.)
- `public/*` - Статичные файлы (шрифты, иконки, и т.д.)
- `package.json` - Манифест проекта.
- `astro.config.mjs` - Конфигурационный файл Astro. (recommended)
- `tsconfig.json` - Конфигурационный файл TypeScript. (recommended)

### Пример дерева проекта

Структура обычного Astro проекта может выглядеть так:

```
├── src/
│   ├── components/
│   │   ├── Header.astro
│   │   └-─ Button.jsx
│   ├── layouts/
│   │   └-─ PostLayout.astro
│   └── pages/
│   │   ├── posts/
│   │   │   ├── post1.md
│   │   │   ├── post2.md
│   │   │   └── post3.md
│   │   └── index.astro
│   └── styles/
│       └-─ global.css
├── public/
│   ├── robots.txt
│   ├── favicon.svg
│   └-─ social-image.png
├── astro.config.mjs
├── package.json
└── tsconfig.json

```

### `src/`

Директория `src/` это место, где живет ваш код. Это включает:

- [Страницы](/ru/core-concepts/astro-pages/)
- [Макеты](/ru/core-concepts/layouts/)
- [Astro компоненты](/ru/core-concepts/astro-components/)
- [Компоненты UI фреймворков](/ru/core-concepts/framework-components/)
- [Стили (CSS, Sass)](/ru/guides/styling/)
- [Markdown](/ru/guides/markdown-content/)

Astro обрабатывает, оптимизирует и бандлит ваши файлы в "src/" для создания веб-сайта, который будет доставлен до браузера.
В отличие от статического каталога `public/`, ваши файлы в `src/` обрабатывает за вас Astro.

Некоторые файлы (например, Astro компоненты) не отправляются в браузер в том виде, в каком они написаны, а вместо этого отображаются в статическом HTML.
Другие файлы (например, CSS) отправляются в браузер, но могут быть оптимизированы или объединены с другими файлами CSS для повышения производительности.

### `src/components`

**Компоненты** - переиспользуемые блоки кода для ваших HTML странииц. 
Это может быть [Astro компонент](/ru/core-concepts/astro-components/),
или [компоненты UI фреймворков](/ru/core-concepts/framework-components/) как React или Vue.  
Обычно все компоненты вашего проекта группируются и упорядочиваются в этой папке.

Это общее соглашение в проектах Astro, но оно не является обязательным. Не стесняйтесь организовывать свои компоненты так, как вам нравится!

### `src/layouts`

[Макеты](/ru/core-concepts/layouts/) это особая категория компонентов, которые помещают некий контент в макет страницы.
Они часто используются [Astro страницами](/ru/core-concepts/astro-pages/) и
[Markdown или MDX страницами](/ru/guides/markdown-content/) для определения макета страницы.

Как и `src/components`, эта директория является общим соглашением, но оно не является обязательным.

### `src/pages`

[Страницы](/ru/core-concepts/astro-pages/) это особая категория компонентов, для создания новых страниц на вашем сайте.
Страницей может быть Astro компонент, или Markdown файл это представляет собой некоторую страницу вашего сайта.

:::caution
`src/pages` это **обязательная** под-директория в вашем Astro проекте. Без него, ваш сайт не будет иметь страниц и роутинга.
:::

### `src/styles`

`src/styles` - директория для хранения ваших CSS или Sass, но оно не является обязательным.
Пока ваши стили находятся где-то в каталоге `src/` и импортируются правильно, Astro будет обрабатывать и оптимизировать их.

### `public/`

Каталог `public/` предназначен для файлов и ресурсов, которые не нужно обрабатывать в процессе сборки Astro.
Эти файлы будут скопированы в папку сборки нетронутыми.

Такое поведение делает `public/` идеальным для общих ресурсов, таких как изображения и шрифты, или особых файлов,
таких как `robots.txt ` и `manifest.webmanifest`.

Вы можете поместить CSS и JavaScript в каталог `public/`, но имейте в виду, что эти файлы не будут объединены 
или оптимизированы в окончательной сборке.

:::tip
Как правило, любой CSS или JavaScript, который вы пишете, должен находиться в директории `src/`.
:::

### `package.json`

Это файл, используемый менеджерами пакетов JavaScript для управления вашими зависимостями.
Он так же определяет скрипты, для запуска Astro (напр.: `npm start`, `npm run build`).

В `package.json` есть [два вида зависимостей](https://docs.npmjs.com/specifying-dependencies-and-devdependencies-in-a-package-json-file):
`dependencies` и `devDependencies`.
В большинстве случаев, они работают одинаково: Astro нужны все зависимости во время сборки, и ваш установщик пакетов установит оба вида зависимостей.
Мы рекомендуем поместить все ваши зависимости в `dependencies` для начала, и используйте "devDependencies", если вы обнаружите в этом особую необходимость.

Если нужна помощь с созданием файла `package.json` в вашем проекте, посмотрите руководство по [ручной установке](/ru/install/manual/).

### `astro.config.mjs`

Этот файл создается в каждом стартовом шаблоне и включает опции конфигурации вашего проекта.
Здесь вы можете указать используемые интеграции, параметры сборки, параметры сервера и многое другое.

Смотрите [Руководство по настройке Astro](/ru/guides/configuring-astro/) для получения подробной информации о настройке конфигураций.

### `tsconfig.json`

Этот файл создается в каждом стартовом шаблоне и включает параметры конфигурации TypeScript для вашего проекта Astro.
Некоторые функции (например, импорт пакетов npm) не полностью поддерживаются в редакторе без файла `tsconfig.json`.

Смотрите [Руководство по настройке TypeScript](/ru/guides/typescript/) для получения подробной информации о настройке конфигураций.