# Main Index

## New Widget

```js
var mainIndex = window.fdc__widget__.WMainIndex.init(selector, initialConfig, initialLanguage, localeMessages);

var mainIndex = window.fdc__widget__.WMainIndex.init('.main-index-widget' /* optional parameters */);
```

- **selector** (_String_): Any valid querySelector
- **initialLanguage** (_String_): Language Code
- **initialConfig** (_Object_): All options can be passed here initially
  - **ric** (_String_): Exchange Symbol
  - **showHeader** (_Boolean_): Toggles the ticker and button visibility
  - **view** (_String_): Toggles initial view ('chart' or 'table')
- **Returns** (_Object_): new widget instance

## API

### `setRic(ric)`

Set instrument code

- **ric** (_String_): Reuters Instrument Code (RIC)
- **Returns** (_void_): void

```js
mainIndex.setRic('BMWG.DE');
```

### `setView(view)`

Set the default view on init

- **view** (_String_): view variant (either 'chart' or 'table'. Defaults to 'chart')
- **Returns** (_void_): void

```js
mainIndex.setView('chart');
```

### `setHeader(header)`

Toggle the widget header containing the price and ticker

- **header** (_Boolean_): Toggle the header on or off. Defaults to 'true'.
- **Returns** (_void_): void

```js
mainIndex.setHeader(true);
```

### `setLocale(locale [, fallback])`

Set new locale for widget instance

- **locale** (_String_): country code
- **fallback** (_String, optional_): country code, fallback to this locale if `locale` is not found in translation strings
- **Returns** (_void_): void

```js
mainIndex.setLocale('no');
```

### `getLocale()`

Get the current active locale for widget instance.

- **Returns** (_String_): country code

```js
mainIndex.setLocale('no');
```

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(locale, messages)`

Add new messages to existing locale or add new locale with messages.

```js
mainIndex.setLocaleMessages('en', {
  buttons: {
    chart: 'Chart',
    table: 'Table'
  },
  table: {
    high: 'High',
    low: 'Low',
    volume: 'Volume',
    '1week': '1 week',
    '1month': '1 month',
    '3months': '3 months',
    '6months': '6 months',
    '1year': '1 year',
    yearToDate: 'Year to date'
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
mainIndex.destroy();
```
