# 🔌 Огляд API платформи VotePulse

Цей документ містить опис базових ендпоінтів REST API для інтеграції з платформою голосувань VotePulse.

---

## 📌 Базовий URL
`https://api.votepulse.com/v1`

---

## 🚀 Ендпоінти

### 1. Отримання списку активних опитувань
Отримує перелік усіх publicly доступних опитувань.

* **HTTP Метод:** `GET`
* **Ендпоінт:** `/polls`
* **Приклад запиту:**
  ```http
  GET /v1/polls HTTP/1.1
  Host: api.votepulse.com
  Authorization: Bearer YOUR_API_KEY

  Успішна відповідь (200 OK):
  [
  {
    "id": "poll_101",
    "title": "Вибір дати релізу",
    "status": "active",
    "total_votes": 42
  },
  {
    "id": "poll_102",
    "title": "Кращий дизайн логотипу",
    "status": "active",
    "total_votes": 128
  }
]

### 2.Створення нового опитування
Створює нове голосування в системі.

HTTP Метод: POST

Ендпоінт: /polls

Приклад запиту (JSON):
{
  "title": "Яку мову програмування обрати?",
  "options": ["Python", "JavaScript", "Go"],
  "is_private": false
}
Успішна відповідь (201 Created):
{
  "id": "poll_103",
  "title": "Яку мову програмування обрати?",
  "options": ["Python", "JavaScript", "Go"],
  "created_at": "2026-10-26T16:00:00Z",
  "share_url": "[https://votepulse.com/p/poll_103](https://votepulse.com/p/poll_103)"
}

## ⚠️ Коди помилок та відповідей

| Код | Статус | Опис |
| :--- | :--- | :--- |
| **200** | OK | Запит виконано успішно. |
| **201** | Created | Ресурс успішно створено. |
| **400** | Bad Request | Невірний формат даних у запиті (наприклад, відсутній заголовок). |
| **401** | Unauthorized | Токен авторизації відсутній або недійсний. |
| **404** | Not Found | Опитування з вказаним ID не знайдено. |
| **500** | Internal Error | Внутрішня помилка сервера. |

