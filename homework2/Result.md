
### 1. Продукты - Products
* _id_ - Идентификатор продукта PRIMARY KEY
* _name_ - Наименование NOT NULL
* _description_ - Описание - может не быть описания
* _price_id_ - Цена (FK Price.price_id) NOT NULL, CHECK(price_id > 0)
* _category_id_ - Категория (FK categories.id) NOT NULL, CHECK (category_id > 0)
* _maker_id_ - Производитель (FK makers.id) NOT NULL, CHECK(maker_id > 0)
* _provider_id_ - Поставщик (FK Providers.id) - может не быть поставщика

Кардинальность полей:
* _id_ - высокая
* _name_ - высокая
* _description_ - высокая
* _price_id_ - высока
* _category_id_ - низкая
* _maker_id_ - высокая
* _provider_id_ - низкая

Индексы: 
* name_price - поиск по названию и цене (например, продукт с низкой стоимостью)
* name_maker_id - поиск по названию и производителю (например, продукт с от конкретного производителя)
* name_category_id - поиск по названию и категории (например, продукт с категорией Y)

### 2. Категории - Categories
* _id_ - Идентификатор категории PRIMARY KEY
* _name_ - Наименование категории NOT NULL

Кардинальность полей:
* _id_ - высокая
* _name_ - высокая

Индексы: 
* индексы не нужны

### 3. Цена - Price
* _id_ - Идентификатор цены PRIMARY KEY
* _value_ - Значение NOT NULL, CHECK(value >= 0)
* _currency_ - Валюта NOT NULL, (CHECK enum - US, RUB, EURO)
* _discount_ - Скидка - может не быть скидки

Кардинальность полей:
* _id_ - высокая
* _value_ - высокая
* _currency_ - низкая
* _discount_ - низкая

Индексы: 
* value_currency - цена определенной валюты

### 4. Поставщики - Providers
* _id_ - Идентификатор поставщика PRIMARY KEY
* _name_ - Наименование NOT NULL
* _address_id_ - Адрес поставищка (FK Addreses.id), NOT NULL CHECK(address_id > 0)
* _description_ - Описание организации - может быть без описания
* _license_ - Лицензия - может быть без лицензии

Кардинальность полей:
* _id_ - высокая
* _name_ - высокая
* _address_id_ - высокая
* _description_ - высокая
* _license_ - низкая

Индексы: 
* name_adress_id - поставщик по определенному адресу

### 5. Производители - Makers
* _id_ - Идентификатор производителя PRIMARY KEY
* _name_ - Наименование  NOT NULL
* _address_id_ - Адрес производителя (FK addreses.id) NOT NULL, CHECK(address_id > 0)
* _description_ - Описание организации - может быть без описания
* _license_ - Лицензия - может быть без лицензии

Кардинальность полей:
* _id_ - высокая
* _name_ - высокая
* _address_id_ - высокая
* _description_ - высокая
* _license_ - низкая

Индексы: 
* name_adress_id - производитель по определенному адресу


### 6. Адреса - Addresses
* _id_ - Идентификатор адреса PRIMARY KEY
* _country_ - Страна NOT NULL
* _city__ - Город NOT NULL
* _street_ - Улица NOT NULL
* _house_ - Номер дома/офиса NOT NULL, CHECK(house > 0)
* _postcode_ - Почтовый индекс NOT NULL, CHECK(postcode > 0) 

Кардинальность полей:
* _id_ - высокая
* _country_ - низкая
* _city_ - высокая
* _street_ - высокая
* _house_ - низкая
* _postcode_ - высокая

Индексы: 
* street_city_country - адрес по конкретным улице, городу, стране

### 7. Покупатели - Buyers
* _id_ - Идентификатор покупателя PRIMARY KEY
* _name_ - Наименование  NOT NULL
* _address_id_ - Адрес доставки NOT NULL, CHECK(address_id > 0)
* _gender_ - Пол NOT NULL, CHECK( enum M, W)
* _age_ - возраст NOT NULL, CHECK(age > 0)
* _search_querie_id_ - Поисковой запрос (FK Search_queries.id) - может не быть запросов

Кардинальность полей:
* _id_ - высокая
* _name_ - высокая
* _address_id_ - высокая
* _gender_ - низкая
* _age_ - низкая
* _search_queri_id_ - высокая

Индексы: 
* search_query_id_gender - запросы по половому критерию
* search_query_id_age - запросы по возрастному критерию

### 8. Покупки - Purchases
* _id_ - Идентификатор покупки PRIMARY KEY
* _name_ - Наименование покупки NOT NULL
* _buyer_id_ - Идентификатор покупателя (FK buyers.id) NOT NULL, CHECK(buyer_id > 0)
* _product_id_ - Идентификатор продукта (FK products.id) NOT NULL, CHECK(product_id > 0)
* _date_ - Дата покупки NOT NULL, CHECK(format date) 
* _address_delivery_id_ - Адрес доставки (FK addresses.id) - может быть самовывоз
* _guarantee_ - Гарантия - может не быть гарантии

Кардинальность полей:
* _id_ - высокая
* _name_ - высокая
* _buyer_id_ - высокая
* _product_id_ - высокая
* _date_ - высокая
* _address_delivery_id_ - высокая
* _guarantee_ - низкая

Индексы: 
* product_id_buyer_id - какие продукты покупают конкретные покупатели
* date_product_id - продажа продуктов в определенную дату (например, черная пятница)
* address_delivery_id_product_id - из каких районов чаще поступают заказы

### 9. Поисковые запросы - Search_queries
* _id_ - Идентификатор покупателя PRIMARY KEY
* _count_ - Кол-во запросов NOT NULL, CHECK (count>=0)
* _link_ - Ссылка запроса - может не быть ни одной ссылки

Кардинальность полей:
* _id_ - высокая
* _count_ - высокая
* _link_ - низкая

Индексы: 
* count_link - по каким ссылкам чаще всего переходят пользователи (аналитика)


## Примеры бизнес-задас:
* Заказ товара
* Исследование роста продаж 
* Аналитика поисковых запросов
* Расширение ассортимента
