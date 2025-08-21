# Страница интернет-магазина

![CI](https://github.com/NMYurchenko-max/ra-webstore-fc/actions/workflows/web.yml/badge.svg)

[deploy](https://nmyurchenko-max.github.io/ra-webstore-fc/)

## Задание
Необходимо создать React-компонент ShopItemFunc (функциональный компонент), с помощью которого мы могли бы реализовывать представление информации о товарах из нашего каталога на сайте в таком виде (компонент обведён пунктирной линией):
![Страница интернет-магазина](pic/preview.png)

### Пример использования

```jsx
const item = {
  brand: 'Tiger of Sweden',
  title: 'Leonard coat',
  description: 'Minimalistic coat in cotton-blend',
  descriptionFull: 'Men\'s minimalistic overcoat in cotton-blend. Features a stand-up collar, concealed front closure and single back vent. Slim fit with clean, straight shape. Above-knee length.',
  price: 399,
  currency: '£'
}

// Внутри компонента App
return (
  <div className="container">
    <div className="background-element">
    </div>
    <div className="highlight-window">
      <div className='highlight-overlay'></div>
    </div>
    <div className="window">
      <ShopItemFunc item={item} />
    </div>
  </div>
)
```
Описание компонента
Компонент должен иметь один параметр props item, в котором он ожидает увидеть объект с информацией о товаре со следующими свойствами:

`brand` — название производителя товара;
`title` — название товара;
`description` — краткое описание товара;
`descriptionFull` — подробное описание товара;
`price` — цена товара;
`currency` — валюта товара.
Компонент должен создавать элемент DOM следующей структуры:
```html
<div class="main-content">
  <h2>Tiger of Sweden</h2>
  <h1>Leonard coat</h1>
  <h3>Minimalistic coat in cotton-blend</h3>
  <div class="description">
    Men's minimalistic overcoat in cotton-blend. Features a stand-up collar, concealed front closure and single back vent. Slim fit with clean, straight shape. Above-knee length.
  </div>
  <div class="highlight-window mobile"><div class="highlight-overlay"></div></div>
  <div class="divider"></div>
  <div class="purchase-info">
    <div class="price">£399.00</div>
    <button>Добавить в корзину</button>
  </div>
</div>
```

Соответственно, название производителя необходимо указать в h2, название товара — в h1, краткое описание — в h3, подробное описание — в div.description, цену и валюту — в div.price. При этом символ валюты должен стоять перед ценой, а цена должна быть указана с двумя знаками после запятой.

### Реализация (Проект React+Vite)

Проект состоит из одного файла index.js, в котором находится реализация компонента ShopItemFunc.
 Для item можете использовать либо тип object, либо вынести item в класс и использовать instanceOf.

Используйте расположенный в этом каталоге CSS для стилизации.

```jsx
import React from 'react';

const ShopItemFunc = ({ item }) => {
  return (
    <div className="main-content">
      <h2>{item.brand}</h2>
      <h1>{item.title}</h1>
      <h3>{item.description}</h3>
      <div className="description">{item.descriptionFull}</div>
      <div className="highlight-window mobile">
        <div className="highlight-overlay"></div>
      </div>
      <div className="divider"></div>
      <div className="purchase-info">
        <div className="price">{item.currency}{item.price.toFixed(2)}</div>
        <button>Добавить в корзину</button>
      </div>
    </div>
  );
};

export default ShopItemFunc;
