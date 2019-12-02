# Winners Losers

## New Widget

```js
var winnerLosers = window.fdc__widgets__.WWinnersLosers.init(selector, initialLanguage, initialConfig);

var winnersLosers = window.fdc__widgets__.WWinnersLosers.init('.widgetWinnersLosers');
```

- **selector** (_String_): Any valid querySelector
- **initialLanguage** (_String_): Language Code
- **initialConfig** (_Object_):
  - **exchange** (_String_): Exchange name. Choices are: Oslo, Stockholm, Helsinki, Copenhagen, Nordic
  - **table** (_String_): Table variant. Choices are: gainers, losers, mostvolume, mosttrades, mostturnover. Visually gainers and losers are the same but sort differs. Also mosttrades, mostvolume and mostturnover are visually the same but sorted diffently.
  - **results** (_String_): Number of results
- **Returns** (_Object_): new widget instance

## API

### `setExchange(exchange)`

Set new exchange name

- **exchange** (_String_): exchange name i.e. 'Oslo'
- **Returns** (_void_): void

```js
winnersLosers.setExchange('Oslo');
```

### `setTable(table)`

Set table variation (gainers, losers, mostvolume, mosttrades, mostturnover)

- **table** (_String_): table variant
- **Returns** (_void_): void

```js
winnersLosers.setTable('gainers');
```

### `setResults(results)`

Set the number of returned results

- **results** (_Number_): any number
- **Returns** (_void_): void

```js
winnersLosers.setResults(5);
```

### `onBuy(handler)`

Registers callback function to listen for the buy button click events

- **function** (_Function_): callBack function triggered by click event
- **event** (_Object_): Event Object
  - **data** (_Object_): Data / Payload
    - **ric** (_String_): Reuters Instrument Code (e.g. 'AAPL.OQ')
  - **origin** (_Object_): the original click event
- **Returns** (_void_): void

```js
function myHandler(event) {
  console.log('Buy event!: ' + event.data.ric);
}
winnersLosers.onBuy(myHandler);
```

### `setLocale(locale [, fallback])`

Set new locale for widget instance

- **locale** (_String_): country code
- **fallback** (_String, optional_): country code, fallback to this locale if `locale` is not found in translation strings
- **Returns** (_void_): void

```js
winnersLosers.setLocale('no');
```

### `getLocale()`

Get the current active locale for widget instance.

- **Returns** (_String_): country code

```js
winnersLosers.setLocale('no');
```

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(locale, messages)`

Add new messages to existing locale or add new locale with messages.

```js
winnersLosers.setLocaleMessages('no', {
  controls: {
    labels: {
      exchange: 'Utveksling',
      table: 'Bord',
      interval: 'Intervall',
      results: 'Resultater',
      min: 'Min',
      display: 'Display',
      gainers: 'Vinnere',
      losers: 'Tapere',
      mostActive: 'Mest handlet'
    }
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

### `destroy()`

Destroy widget instance and remove it from DOM

- **Returns** (_void_): void

```js
winnersLosers.destroy();
```
