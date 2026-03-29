### Запрос списка магазинов партнёров
```GET /api/v1/partner-stores```
Простой GET-метод, получающий список доступных магазинов. Их список и время доставки зависят от адреса пользователя, но предполагаем, что эти данные передаются при входе в приложение либо на отдельном экране, и здесь используем уже сохранённый на сервере адрес пользователя.
Вызов выглядит примерно так:
```GET https://petrushka.ru/api/v1/partner-stores
Content-Type: application/json
Authorization: Bearer <token>
```

### Пример ответа
```json
{
  "stores": [
    {
      "id": "vkusvill",
      "title": "ВкусВилл",
      "delivery_type": "fast",
      "delivery_min_minutes": 20,
      "delivery_max_minutes": 60,
      "logo_url": "https://petrushka.ru/img/partners/vkusvill.png",
      "external_url": "https://vkusvill.ru"
    },
    {
      "id": "victoria",
      "title": "ВИКТОРИЯ",
      "delivery_type": "nearest",
      "delivery_start": "2026-03-29T17:00:00+03:00",
      "delivery_end": "2026-03-29T19:00:00+03:00",
      "logo_url": "https://petrushka.ru/img/partners/viktoria.png",
      "external_url": "https://viktoria.ru"
    }
  ]
}
```
#### Описание полей
stores - массив данных о магазинах партнёров. Содержит следующие поля:
1. id - идентификатор магазина. Для примера использовал просто транслитерированные названия, но это может быть неудобно на случай последующего переименования магазина. Можно рассмотреть другие форматы идентификаторов
2. title - наименование магазина для отображения
3. delivery_type - флаг типа доставки, быстрая/ближайшая
4. delivery_min_minutes - минимальное время быстрой доставки
5. delivery_max_minutes - максимальное время быстрой доставки
6. delivery_start - минимальный timestamp ближайшей доставки
7. delivery_end - максимальный timestamp ближайшей доставки
8. logo_url - url логотипа магазина
9. external_url - url внешнего ресурса
