# Калейдоскоп - сайт турагента

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

### 3. SEO-оптимизация

#### 3.1. Мета-теги
В `public/index.html`:
```html
<meta name="description" content="Описание Вашего сайта">
<meta name="keywords" content="ключевые слова">
<title>Название сайта</title>
```

#### 3.2. Маршрутизация
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

### 4. Размещение сайта

#### 4.1. Подготовка к деплою
```bash
npm run build
```
