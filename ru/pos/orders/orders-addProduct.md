## orders.addProduct: добавить товар или тех. карту к заказу

> Пример добавления товара без модификации:

```javascript
Poster.orders.addProduct(1503219480866, {id: 1})
```

> Пример добавления товара с модификацией:

```javascript
Poster.orders.addProduct(1503219480866, {id: 1, modification: 1})
```

> Пример добавления тех. карты с модификацией:

```javascript
Poster.orders.addProduct(1503219480866, {
    id: 1, 
    modification: '[{"m":1,"a":1}]'
})
```

Метод добавляет товар или тех. карту к заказу. Товар всегда добавляется с количеством 1.
Чтобы изменить кол-во товара используйте метод [orders.changeProductCount](/docs/v3/pos/orders/orders-changeProductCount).

### Аргументы

Аргумент | Описание
-------- | --------
1-й, id | ID заказа (unix-timestamp в миллисекундах)
2-й, product | Объект со свойствами товара который добавляем к заказу

Объект `product` должен содержать следующие свойства

Свойство | Описание
-------- | --------
id | Обязательный параметр, id товара 
modification | Id модификации. Обязательный параметр, если товар с модификацией. Может быть числом если это товар или строкой если это тех. карта с модификациями. 


### Ответ

Метод возвращает `Promise` результат которого объект со следующими свойствами: 

Свойство | Описание
-------- | --------
order | Объект типа [Order](/docs/v3/pos/types/order), с обновленным списком товаров 