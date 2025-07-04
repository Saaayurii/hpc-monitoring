# 🔋 DataCenter Energy Calculator

**Калькулятор энергопотребления центров обработки данных суперкомпьютеров**

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/username/datacenter-calculator-frontend)
[![Railway Deploy](https://railway.app/button.svg)](https://railway.app/template/datacenter-api)

> Веб-приложение для расчета и анализа энергоэффективности ЦОД с интерактивными графиками и рекомендациями по оптимизации.

Разработан в рамках **III Всероссийской школы-семинара НЦФМ** "Центр исследования архитектур суперкомпьютеров"

---

## 🎯 О проекте

### Проблема
- Современные суперкомпьютеры потребляют 10-30 МВт электроэнергии
- Стоимость электроэнергии достигает 40% операционных расходов ЦОД
- ЦОД производят ~4% глобальных выбросов CO₂

### Решение
Инструмент для оптимизации энергоэффективности на этапе проектирования с расчетом ключевых метрик:

| Метрика | Описание | Оптимальное значение |
|---------|----------|---------------------|
| **PUE** | Power Usage Effectiveness | < 1.2 |
| **DCiE** | Data Center infrastructure Efficiency | > 80% |
| **CUE** | Carbon Usage Effectiveness | < 0.5 |

---

## ⚡ Демо

🌐 **Live Demo:** [datacenter-calculator.vercel.app](https://datacenter-calculator.vercel.app)  
📚 **API Docs:** [api.datacenter-calculator.com/docs](https://api.datacenter-calculator.com/docs)

---

## 🛠 Технологии

### Frontend
- **Next.js 14** (App Router) + **TypeScript**
- **Tailwind CSS** + **Recharts** для графиков
- **React Hook Form** + **Zod** для валидации

### Backend
- **FastAPI** + **Python 3.11**
- **SQLAlchemy** + **Pydantic**
- **NumPy/Pandas** для научных вычислений

### Развертывание
- **Database:** Neon PostgreSQL (бесплатно)
- **Backend:** Railway (бесплатно)
- **Frontend:** Vercel (бесплатно)

---

## 🚀 Быстрый старт

### Локальная разработка

```bash
# Клонирование
git clone https://github.com/username/datacenter-energy-calculator.git
cd datacenter-energy-calculator

# Frontend
cd frontend
npm install
cp .env.example .env.local
npm run dev  # http://localhost:3000

# Backend
cd backend
python -m venv venv
source venv/bin/activate  # Linux/Mac
pip install -r requirements.txt
cp .env.example .env
uvicorn app.main:app --reload  # http://localhost:8000
```

### Облачное развертывание

#### 1. База данных (Neon)
```bash
# 1. Создать проект на https://neon.tech
# 2. В SQL Editor выполнить database/init.sql
# 3. Сохранить строку подключения
```

#### 2. Backend (Railway)
```bash
# 1. Создать репозиторий backend на GitHub
# 2. Подключить к https://railway.app
# 3. Настроить переменные:
DATABASE_URL=<neon_connection_string>
SECRET_KEY=your-secret-key
ENVIRONMENT=production
```

#### 3. Frontend (Vercel)
```bash
# 1. Создать репозиторий frontend на GitHub  
# 2. Импортировать в https://vercel.com
# 3. Настроить переменную:
NEXT_PUBLIC_API_URL=https://your-backend.railway.app
```

---

## 📊 Функции

### ✨ Основные возможности
- 🧮 **Расчет энергометрик** (PUE, DCiE, CUE)
- 📊 **Интерактивные графики** распределения энергопотребления
- 🔄 **Сравнение архитектур** охлаждения
- 🌍 **Анализ углеродного следа**
- 💡 **Рекомендации по оптимизации**
- 📈 **Сравнение с эталонами** (TOP-500 суперкомпьютеры)
- 📄 **Экспорт отчетов** в PDF и Excel

### 🎯 Целевая аудитория
- Исследователи суперкомпьютерных технологий
- Инженеры ЦОД и системные архитекторы
- Студенты технических специальностей
- IT-менеджеры и технические директора

---

## 📚 API

### Основные endpoints

```javascript
// Расчет метрик энергоэффективности
POST /api/v1/calculate
{
  "itInfrastructure": {
    "serverCount": 100,
    "cpuType": "x86",
    "powerPerServer": 0.5,
    "loadFactor": 70,
    "efficiency": 85,
    "networkPower": 5.0,
    "storagePower": 3.0
  },
  "coolingSystem": {
    "coolingType": "liquid",
    "ambientTemperature": 25,
    "targetTemperature": 18,
    "copEfficiency": 3.5,
    "redundancy": 20
  },
  // ... остальные параметры
}

// Получение эталонных данных
GET /api/v1/benchmarks/supercomputer

// Сохранение конфигурации
POST /api/v1/configurations
```

**Полная документация:** `/docs` (Swagger UI)

---

## 🧮 Математические модели

### Базовые формулы

```python
# PUE (Power Usage Effectiveness)
PUE = Total_Facility_Power / IT_Equipment_Power

# DCiE (Data Center infrastructure Efficiency)  
DCiE = (1 / PUE) × 100%

# CUE (Carbon Usage Effectiveness)
CUE = Total_CO2_Emissions / IT_Equipment_Power
```

### Компоненты энергопотребления
- **IT-оборудование:** 40-50%
- **Система охлаждения:** 30-40%
- **Система питания:** 10-15%
- **Освещение и прочее:** 5-10%

---

## 📈 Эталонные данные

База данных содержит 21 эталонный ЦОД:

| Система | Тип | PUE | Охлаждение | Страна |
|---------|-----|-----|------------|---------|
| Fugaku (RIKEN) | Суперкомпьютер | 1.02 | Жидкостное | Япония |
| Frontier (ORNL) | Суперкомпьютер | 1.03 | Жидкостное | США |
| Christofari Neo | Суперкомпьютер | 1.15 | Жидкостное | Россия |
| Google Finland DC | Корпоративный | 1.09 | Воздушное | Финляндия |
| Yandex DataCenter | Облачный | 1.35 | Воздушное | Россия |

---

## 🏗 Структура проекта

```
datacenter-energy-calculator/
├── frontend/                # Next.js приложение
│   ├── src/app/            # App Router pages
│   ├── src/components/     # React компоненты
│   ├── src/lib/           # API клиент и утилиты
│   └── package.json
├── backend/                # FastAPI приложение
│   ├── app/api/           # API endpoints
│   ├── app/models/        # SQLAlchemy модели
│   ├── app/services/      # Бизнес-логика
│   ├── requirements.txt
│   └── railway.json       # Railway конфигурация
├── database/
│   └── init.sql          # Схема БД и тестовые данные
└── README.md
```

---

## 🔧 Конфигурация

### Environment Variables

#### Frontend (.env.local)
```bash
NEXT_PUBLIC_API_URL=http://localhost:8000
```

#### Backend (.env)
```bash
DATABASE_URL=postgresql://user:pass@host/db
SECRET_KEY=your-super-secret-key
ENVIRONMENT=development
```

---

## 🧪 Тестирование

### Проверка API
```bash
# Health check
curl https://your-backend.railway.app/health

# Тестовый расчет
curl -X POST "https://your-backend.railway.app/api/v1/calculate" \
  -H "Content-Type: application/json" \
  -d '{"itInfrastructure": {...}}'
```

### Лимиты бесплатных планов
- **Neon:** 3 GB storage, 100 часов compute
- **Railway:** 512 MB RAM, 100 GB трафика
- **Vercel:** 100 GB bandwidth, unlimited deployments

---

## 🤝 Вклад в проект

1. Fork репозитория
2. Создать feature branch (`git checkout -b feature/amazing-feature`)
3. Commit изменений (`git commit -m 'Add amazing feature'`)
4. Push в branch (`git push origin feature/amazing-feature`)
5. Создать Pull Request

---

## 📄 Лицензия

Этот проект лицензирован под MIT License - см. файл [LICENSE](LICENSE) для деталей.

---

## 👥 Авторы

- **Роман Долженко** - Frontend разработка (JavaScript/V8) - [@username](https://github.com/username)
- **Денис Гришин** - Backend разработка (Python) - [@username](https://github.com/username)

**Проект разработан в рамках III Всероссийской школы-семинара НЦФМ**

---

## 🙏 Благодарности

- **НЦФМ** за возможность представить исследование
- **Академик И.А. Каляев** за вдохновение работами по реконфигурируемым архитектурам
- Сообщество разработчиков открытого ПО

---

**⭐ Если проект полезен, поставьте звезду!**
