# Price Chart

## New Widget

```js
var priceChart = window.fdc__widget__.WPriceChart.init(selector, initialConfig, initialLanguage, localeMessages);

var priceChart = window.fdc__widget__.WPriceChart.init('.price-chart-widget' /* optional parameters */);
```

- **selector** (_String_): Any valid querySelector
- **initialLanguage** (_String_): Language Code
- **initialConfig** (_Object_): All options can be passed here initially
  - **ric** (_String_): Exchange Symbol
  - **showVolume** (_Boolean_): Toggles the volume chart visibility
- **Returns** (_Object_): new widget instance

## API

### `setRic(ric)`

Set instrument code

- **ric** (_String_): Reuters Instrument Code (RIC)
- **Returns** (_void_): void

```js
priceChart.setRic('BMWG.DE');
```

### `setShowVolume(showVolume)`

Set the default view on init

- **showVolume** (_String_): Toggle the volume chart on or off. Defaults to 'true'.
- **Returns** (_void_): void

```js
priceChart.setShowVolume(false);
```

### `setLocale(locale [, fallback])`

Set new locale for widget instance

- **locale** (_String_): country code
- **fallback** (_String, optional_): country code, fallback to this locale if `locale` is not found in translation strings
- **Returns** (_void_): void

```js
priceChart.setLocale('no');
```

### `getLocale()`

Get the current active locale for widget instance.

- **Returns** (_String_): country code

```js
priceChart.getLocale('no');
```

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(locale, messages)`

Add new messages to existing locale or add new locale with messages.

```js
priceChart.setLocaleMessages('en', {
  controls: {
    symbol: "RIC",
    intraday: "Intraday",
    historical: "Historical",
    dateFrom: "From",
    dateTo: "To"
  },
  messages: {
    nodata: "No data available for this exchange. Probably not operating at this time.",
    error: "There was an error. We will try to get the data again in a few moments..."
  }
});
```

### `destroy()`

Destroy widget instance and remove it from DOM

- **Returns** (_void_): void

```js
priceChart.destroy();
```
