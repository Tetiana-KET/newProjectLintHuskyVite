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
_eslint-plugin-jsx-a11y- правила касающиеся доступности для людей с огр.возм.\*_
_eslint-plugin-prettier и сам prettier для работы притиер_

- создать файл с настройками **.eslintrc.json**

**если с webpack**

- npm i -D ts-loader (лоадер TS для webpack-а - чтобы webpack мог работать с .ts файлами)
- npm i -D eslint-webpack-plugin (плагин ESlint - для работы ESlint вместе с Webpack)

## 4. Устанавливаем Prettier

- **npm install --save-dev --save-exact prettier**
- create file **.prettierrc**
- create file **.prettierignore**

## 5. Настраиваем Husky и Lint staged

- Install husky and lint-staged:
  **npm install --save-dev husky lint-staged**
  **npx husky init**
- Note: If you use ESLint, make sure lint-staged runs it before Prettier, not after.

## 6. validate-branch-name

- **npm install validate-branch-name -D**
- https://www.npmjs.com/package/validate-branch-name

  https://github.com/Jeneko/News-api-migration-walkthrough
  _стайлинт - опционально, нужно разобраться_
