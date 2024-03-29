https://gist.github.com/TELEUZI/410d19772481d98b06e0b41ebf89fff1
**npm init -y** для создания файла package.json
**npm i** установки исходных зависимостей проекта если скопировала файлы

## 1. Vite

- **npm init vite@latest**
- выбрала vanilla
- выбрала typescript
- создаем **vite.config.ts**

## 2. Добавляем TS

npm i -D typescript
Создаем файл **tsconfig.json** - команда **npx tsc --init**

## 3. Добавляем Eslint

- **npm install --save-dev eslint**
- **npm i -D @typescript-eslint/parser** (парсер TS для ESlint - чтобы ESlint умел правильно парсить .ts файлы)
- **npm i -D @typescript-eslint/eslint-plugin** (плагин TS для ESlint - правила, по которым ESlint будет проверять .ts файлы)
- **npm install --save-dev eslint-config-airbnb eslint-config-prettier eslint-plugin-html eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-prettier prettier**

_eslint-config-prettier для правильной совместной работы prettier и eslint_
_eslint-config-airbnb - стайл гайд_
_eslint-plugin-html - линтить ошибки в теге скрипт_
_eslint-plugin-import - поддерживать синтаксис импорт/экспорт_
_eslint-plugin-jsx-a11y- правила касающиеся доступности для людей с огр.возм_
_eslint-plugin-prettier и сам prettier для работы притиер_

- создать файл с настройками **.eslintrc.json**

**если с webpack**

- npm i -D ts-loader (лоадер TS для webpack-а - чтобы webpack мог работать с .ts файлами)
- npm i -D eslint-webpack-plugin (плагин ESlint - для работы ESlint вместе с Webpack)

## 4. Устанавливаем Prettier

- **npm install --save-dev --save-exact prettier**
- create file **.prettierrc**
- create file **.prettierignore**

## 5. Настраиваем Husky и Lint staged и validate-branch-name

- Install husky and lint-staged:
  **npm install --save-dev husky lint-staged**
  **npx husky init**
  - **"prepare": "cd .. && husky rss-puzzle/.husky" в package.json**
  - npm run prepare - выполнить в терминале 1 раз
 - **.lintstagedrc.json** создать файл
    ` {
      "./src/.": ["npm run ci:format"],
      "./src/**.*": ["npm run format"]
    `}

    *изза вложенностей нужно поправить пути*
    `{
      "./src/.": ["npm run ci:format"],
      "./src/**/*.*": ["npm run format"]
    }
    `
 - **npm install validate-branch-name -D**
 - **.validate-branch-namerc.json** создать файл

 `
  {
    "pattern": "^(feat|fix|chore|refactor)/RSS-PZ-(0\\d|\\d+)_\\w+",
    "errorMsg": "Branch name doesn't follow the defined repository rules"
  }
`
- Note: If you use ESLint, make sure lint-staged runs it before Prettier, not after.
- в pre-commit и pre-push удали вот это - #! - это коммент

файл pre-commit
cd rss-puzzle - перейти в папку
npx lint-staged

файл pre-push
cd rss-puzzle
npx validate-branch-name


- https://www.npmjs.com/package/validate-branch-name

  https://github.com/Jeneko/News-api-migration-walkthrough
  _стайлинт - опционально, нужно разобраться_


## DEPLOY

 в вите конфиг
```import { defineConfig } from 'vite';

export default defineConfig({
  css: {
    modules: {
      localsConvention: 'camelCase',
    },
  },
  base: '',
});```

В package.json добавить

"deploy": "npm run build && npx gh-pages -d dist -e rss-puzzle"

в терминале просто запускаешь
npm install gh-pages --save-dev
npm run deploy
все. весь деплой