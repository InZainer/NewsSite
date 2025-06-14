# Kaleidoscope Travel Agency Website

## Установка и настройка

### 1. Установка и настройка окружения

#### 1.1. Установка Node.js и npm
- Убедитесь, что на Вашем компьютере установлены Node.js и npm. Вы можете скачать их с официального сайта Node.js.

#### 1.2. Создание нового проекта
```bash
npx create-react-app my-portfolio
cd my-portfolio
```

#### 1.3. Установка зависимостей
```bash
npm install react-router-dom i18next react-i18next i18next-browser-languagedetector
```

#### 1.4. Запуск проекта
```bash
npm start
```
Теперь сайт будет доступен по адресу http://localhost:3000.

### 2. Структура проекта

```
src/
├── assets/         # Изображения и другие медиафайлы
├── components/     # React компоненты
├── pages/         # Страницы приложения
├── styles/        # CSS стили
├── locales/       # Файлы локализации
├── i18n.js        # Конфигурация интернационализации
└── App.jsx        # Главный компонент приложения

public/
├── index.html     # Основной HTML файл
├── favicon.ico    # Иконка сайта
├── manifest.json  # Манифест для PWA
└── robots.txt     # Файл для поисковых роботов
```

### 3. Добавление и редактирование контента

#### 3.1. Добавление нового языка
1. Создать новый файл в папке `locales/` (например, `en.json`)
2. Добавить переводы в формате:
```json
{
  "menu": {
    "news": "News",
    "services": "Services",
    "tours": "Tours",
    "about": "About",
    "contact": "Contact"
  }
}
```
3. Добавить новый язык в `i18n.js`:
```javascript
import enTranslations from './locales/en.json';

i18n.addResourceBundle('en', 'translation', enTranslations);
```

#### 3.2. Создание нового компонента
```javascript
// src/components/NewComponent.jsx
import React from 'react';
import { useTranslation } from 'react-i18next';
import styles from '../styles/NewComponent.module.css';

const NewComponent = () => {
  const { t } = useTranslation();
  
  return (
    <div className={styles.container}>
      <h2>{t('newComponent.title')}</h2>
      <p>{t('newComponent.description')}</p>
    </div>
  );
};

export default NewComponent;
```

#### 3.3. Добавление стилей
```css
/* src/styles/NewComponent.module.css */
.container {
  padding: 20px;
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
```

### 4. SEO-оптимизация

#### 4.1. Мета-теги
В `public/index.html`:
```html
<meta name="description" content="Описание Вашего сайта">
<meta name="keywords" content="ключевые слова">
<title>Название сайта</title>
```

#### 4.2. Маршрутизация
```javascript
// src/App.jsx
import { BrowserRouter, Routes, Route } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/news" element={<News />} />
        <Route path="/services" element={<Services />} />
        <Route path="/tours" element={<Tours />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </BrowserRouter>
  );
}
```

### 5. Размещение сайта

#### 5.1. Подготовка к деплою
```bash
npm run build
```

#### 5.2. Настройка CI/CD (GitHub Actions)
Создать файл `.github/workflows/deploy.yml`:
```yaml
name: Deploy
on:
  push:
    branches: [ main ]
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Install Dependencies
        run: npm install
      - name: Build
        run: npm run build
      - name: Deploy
        uses: JamesIves/github-pages-deploy-action@4.1.4
        with:
          branch: gh-pages
          folder: build
```

### 6. Работа с изображениями

#### 6.1. Оптимизация изображений
- Использовать формат WebP для фотографий
- Оптимизировать размер изображений
- Добавлять атрибуты alt для доступности

#### 6.2. Импорт изображений
```javascript
import image from '../assets/image.webp';

function Component() {
  return <img src={image} alt="Description" />;
}
```

### 7. Обновление контента

#### 7.1. Изменение текстов
1. Найти нужный файл локализации в `locales/`
2. Отредактировать соответствующий ключ
3. Перезапустить приложение для применения изменений

#### 7.2. Добавление новых страниц
1. Создать новый компонент в `pages/`
2. Добавить маршрут в `App.jsx`
3. Добавить переводы в файлы локализации
4. Создать стили в `styles/`

### 8. Рекомендации по разработке

- Использовать CSS модули для изоляции стилей
- Следовать принципам семантической верстки
- Регулярно обновлять зависимости
- Тестировать на разных устройствах и браузерах
- Следить за производительностью
- Использовать инструменты разработчика для отладки
