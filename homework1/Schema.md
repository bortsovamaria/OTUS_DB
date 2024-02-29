## Сущности БД

[Схема сущностей БД](Schema_db.png)

### 1. Продукты - Products
* _id_ - Идентификатор продукта
* _name_ - Наименование 
* _description_ - Описание
* _price_id_ - Цена (FK Price.price_id)
* _category_id_ - Категория (FK categories.id)
* _maker_id_ - Производитель (FK makers.id)
* _provider_id_ - Поставщик (FK Providers.id)

### 2. Категории - Categories
* _id_ - Идентификатор категории
* _name_ - Наименование категории

### 3. Цена - Price
* _id_ - Идентификатор цены
* _value_ - Значение 
* _currency_ - Валюта
* _discount_ - Скидка

### 4. Поставщики - Providers
* _id_ - Идентификатор поставщика
* _name_ - Наименование  
* _address_id - Адрес поставищка (FK Addreses.id)
* _description_ - Описание организации
* _license_ - Лицензия

### 5. Производители - Makers
* _id_ - Идентификатор производителя
* _name_ - Наименование  
* _address_id - Адрес производителя (FK addreses.id)
* _description_ - Описание организации
* _license_ - Лицензия

### 6. Адреса - Addresses
* _id_ - Идентификатор адреса
* _country_ - Страна
* _city__ - Город  
* _street_ - Улица
* _house_ - Номер дома/офиса
* _postcode_ - Почтовый индекс

### 7. Покупатели - Buyers
* _id_ - Идентификатор покупателя
* _name_ - Наименование  
* _address_id_ - Адрес доставки
* _gender_ - Пол
* _age_ - возраст
* _search_querie_id_ - Поисковой запрос (FK Search_queries.id)

### 8. Покупки - Purchases
* _id_ - Идентификатор покупки
* _name_ - Наименование покупки
* _buyer_id_ - Идентификатор покупателя (FK buyers.id)
* _product_id_ - Идентификатор продукта (FK products.id)
* _date_ - Дата покупки 
* _address_delivery_id - Адрес доставки (FK addresses.id)
* _guarantee_ - Гарантия

### 9. Поисковые запросы - Search_queries
* _id_ - Идентификатор покупателя
* _count_ - Кол-во запросов  
* _link_ - Ссылка запроса



## Примеры бизнес-задас:
* Заказ товара
* Исследование роста продаж 
* Аналитика поисковых запросов
* Расширение ассортимента
