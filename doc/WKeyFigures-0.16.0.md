# Key Figures

## New Widget

```js
var keyFigures = window.fdc__widget__.WKeyFigures.init(selector, initialConfig, initialLanguage, localeMessages);

var keyFigures = window.fdc__widget__.WKeyFigures.init('.key-figures-widget' /* optional parameters */);
```

- **selector** (_String_): Any valid querySelector
- **initialConfig** (_Object_):
  - **ric** (_String_): RIC (Reuters Instrument Codes)
- **initialLanguage** (_String_): Language Code (currently not used in this widget)
- **localMessages** (_Object_): Translation strings for the language code
- **Returns** (_Object_): new widget instance

## API

### `setRic(ric)`

Set instrument code

- **ric** (_String_): Reuters Instrument Code (RIC)
- **Returns** (_void_): void

```js
keyFigures.setRic('BMWG.DE');
```

### `setLocale(locale [, fallback])`

Set new locale for widget instance

- **locale** (_String_): country code
- **fallback** (_String, optional_): country code, fallback to this locale if `locale` is not found in translation strings
- **Returns** (_void_): void

```js
keyFigures.setLocale('no');
```

### `getLocale()`

Get the current active locale for widget instance.

- **Returns** (_String_): country code

```js
var countryCode = keyFigures.getLocale();
```

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(locale, messages)`

Add new messages to existing locale or add new locale with messages.

```js
keyFigures.setLocaleMessages('en', {
  titles: {
    price: 'Price',
    performance: 'Performance'
  },
  table: {
    vwap: 'VWAP',
    yearHigh: 'Highest price in a year',
    yearLow: 'Lowest price in a year',
    '1day': '1 day',
    '1week': '1 week',
    '1month': '1 month',
    '3months': '3 months',
    '6months': '6 months',
    '1year': '1 year',
    yearToDate: 'Year to date',
    bvps: 'Book value per share',
    eps: 'Earnings per share',
    pe: 'P/E',
    ps: 'P/S',
    salesPerShare: 'Sales per share',
    dividendYield: 'Dividend yield',
    marketCap: 'Market capitalization',
    sharesOutstanding: 'Shares outstanding',
    dividendPerShare: 'Dividend per share',
    dividendDate: 'Dividend date'
  },
  messages: {
    nodata: 'No data available for this exchange. Probably not operating at this time.',
    error: 'There was an error. We will try to get the data again in a few moments...'
  }
});
```

### `destroy()`

Destroy widget instance and remove it from DOM

- **Returns** (_void_): void

```js
keyFigures.destroy();
```
