# Order book

## New Widget

```js
var orderBook = window.fdc__widgets__.orderBook.init(selector, initialConfig, initialLanguage, localeMessages);

var orderBook = window.fdc__widgets__.orderBook.init('.order-book-widget');
```

- **selector** (_String_): Any valid querySelector
- **initialLanguage** (_String_): Language Code
- **initialConfig** (_Object_):
  - **ric** (_String_): ric
  - **hasButtons** (_Boolean_): Show or hide buttons
  - **results** (_String_): Number of rows from 1-10
- **Returns** (_Object_): new widget instance

## API

### `setRic(ric)`

Set new ric

- **ric** (_String_): ric
- **Returns** (_void_): void

```js
orderBook.setRic('BMWG.DE');
```

### `setHasButtons(hasButtons)`

Toggle the buttons on the ask and bid column

- **hasButtons** (_Boolean_): Show or hide sell and buy buttons
- **Returns** (_void_): void

```js
orderBook.setHasButtons(false);
```

### `setResults(results)`

Set the number of returned results, corresponding to the number of rows

- **results** (_Number_): numbers from 1 - 10
- **Returns** (_void_): void

```js
orderBook.setResults(5);
```

### `onBuy(handler)`

Registers callback function to listen for the buy button click events

- **function** (_Function_): callBack function triggered by click event
- **event** (_Object_): Event Object
  - **data** (_Object_): Features all the data from the clicked row. Most importantly probably the ask price.
    - **ask** (_String_): the price of the ask
    - **ask_size** (_String_): the size of the ask
    - **bid** (_String_): the price of the bid
    - **bid_size** (_String_): the size of the bid
    - **level** (_String_): the order book level
    - **num_ask** (_String_): the number of asks on the level
    - **num_bid** (_String_): the number of bids on the level
  - **origin** (_Object_): the event gotten from the grid including the mouse event
- **Returns** (_void_): void

```js
function myHandler(event) {
  console.log('Buy event!: ' + event.data.ask);
}
orderBook.onBuy(myHandler);
```

### `onSell(handler)`

Registers callback function to listen for the sell button click events

- **function** (_Function_): callBack function triggered by click event
- **event** (_Object_): Event Object
  - **data** (_Object_): Features all the data from the clicked row. Most importantly probably the bid price.
    - **ask** (_String_): the price of the ask
    - **ask_size** (_String_): the size of the ask
    - **bid** (_String_): the price of the bid
    - **bid_size** (_String_): the size of the bid
    - **level** (_String_): the order book level
    - **num_ask** (_String_): the number of asks on the level
    - **num_bid** (_String_): the number of bids on the level
  - **origin** (_Object_): the event gotten from the grid including the mouse event
- **Returns** (_void_): void

```js
function myHandler(event) {
  console.log('Sell event!: ' + event.data.bid);
}
orderBook.onSell(myHandler);
```

### `setLocale(locale [, fallback])`

Set new locale for widget instance

- **locale** (_String_): country code
- **fallback** (_String, optional_): country code, fallback to this locale if `locale` is not found in translation strings
- **Returns** (_void_): void

```js
orderBook.setLocale('no');
```

### `getLocale()`

Get the current active locale for widget instance.

- **Returns** (_String_): country code

```js
var localeCode = orderBook.getLocale('no');
```

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(locale, messages)`

Add new messages to existing locale or add new locale with messages.

```js
orderBook.setLocaleMessages('no', {
  buttons: {
    buy: 'K',
    sell: 'S'
  },
  table: {
    symbol: 'Symbol',
    name: 'Navn',
    price: 'Pris',
    priceChange: 'Endring',
    priceChangePercentage: '+/-',
    bid: 'Bud',
    buy: 'Kjøp',
    sell: 'Selge',
    marketCap: 'Mkt Kap (mn)'
  },
  messages: {
    nodata: 'Ingen data tilgjengelig for denne utvekslingen. Sannsynligvis ikke opererer på dette tidspunktet.',
    error: 'Det var en feil. Vi vil prøve å få dataene igjen om noen øyeblikk ...'
  }
});
```

### `showRealtimeSnapshot(jwtToken, successCallback, failureCallback)`

Pass a JWT (JSON Web Token) to the widget. It will then update with realtime data. The success or failure of this procedure will be made clear through callbacks.

- **jwtToken** (_Boolean_): Show or hide sell and buy buttons
- **successCallback** (_Function_): When the snap data is shown you get this callback as confirmation
- **failureCallback(err)** (_Function_): If the snap data is not showing you get this callback with an error message
- **Returns** (_void_): void

```js
function successCallback() {
  console.log('Snap bought!');
}
function failureCallback(err) {
  console.log('Snap data error: ', err);
}
orderBook.showRealtimeSnapshot('1234567890', successCallback, failureCallback);
```

### `destroy()`

Destroy widget instance and remove it from DOM

- **Returns** (_void_): void

```js
orderBook.destroy();
```
