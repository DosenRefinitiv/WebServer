# Ticker Band

## New Widget

```js
var tickerBand = window.fdc__widgets__.WTickerBand.init(selector, initialConfig, initialLanguage, localMessages);

// Example: Initialize widget with default settings
var tickerBand = window.fdc__widgets__.WTickerBand.init('.ticker-band-widget');

// Example: Initialize widget with specific rics to create custom tickers
var tickerBand = window.fdc__widgets__.WTickerBand.init('.ticker-band', {
  tickerElements: [
    { ric: '.OSEBX', name: 'Oslo Børs', img: 'https://www.financial.com/tmp/osebx.jpg' },
    { ric: 'CLc1', name: 'Oljepris', img: 'https://www.financial.com/tmp/clc1.jpg' },
    { ric: '.GDAXI', name: 'Frankfurt DAX', img: 'https://www.financial.com/tmp/gdaxi.jpg' },
    { ric: '.NDX', name: 'Nasdaq', img: 'https://www.financial.com/tmp/ndx.jpg' }
  ],
  truncateNames: true
});
```

- **selector** (_String_): Any valid querySelector
- **initialConfig** (_Object_):
  - **tickerElements** (_Array&lt;Object&gt;_): Array of ticker element objects
    - **ric** (_String_): Reuters Instrument Code (RIC)
    - **name** (_String_): Custom name for the ric. If omitted q._DSPLY_NAME from datafeed will be used.
    - **img** (_String_): Image source url
  - **truncateNames** (_Boolean_): Truncates longer display names
- **initialLanguage** (_String_): Language Code (currently not used in this widget)
- **localMessages** (_Object_): Translation strings for the language code
- **Returns** (_Object_): new widget instance

## API

### `setTickerElements([{tickerElement}, ...])`

Sets new ticker elements during runtime.

```js
// Example: Change rics/ticker after initialisation
tickerBand.setTickerElements([{ ric: 'BMWG.DE' }, { ric: 'AAPL.OQ' }, { ric: 'GOOG.O' }]);
```

- **tickerElement** (_Object_): Array of ticker element objects
  - **ric** (_String_): Reuters Instrument Code (RIC)
  - **name** (_String_): Custom name for the ric. If omitted q._DSPLY_NAME from datafeed will be used.
  - **img** (_String_): Image source url. If omitted no image will be shown.
- **Returns** (_void_): void

### `onClick(function(event))`

Registers callback function to listen for click events

```js
// Example: Get ticker clicks
tickerBand.onClick(function callBack(event) {
  console.log('[API] onClick event from tickerBand. RIC: ', event.ric);
});
```

- **function** (_Function_): callBack function triggered by click event
- **event** (_Object_): Event Object
  - **origin** (_Object_): Original Event
  - **ric** (_String_): Reuters Instrument Code (e.g. 'AAPL.OQ')
- **Returns** (_void_): void

### `setLocale(locale [, fallback])`

Set new locale for widget instance

- **locale** (_String_): country code
- **fallback** (_String, optional_): country code, fallback to this locale if `locale` is not found in translation strings
- **Returns** (_void_): void

```js
tickerBand.setLocale('no');
```

### `getLocale()`

Get the current active locale for widget instance.

- **Returns** (_String_): country code

```js
var countryCode = tickerBand.getLocale();
```

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(locale, messages)`

Add new messages to existing locale or add new locale with messages.

### `destroy()`

Destroy widget instance and remove it from DOM

- **Returns** (_void_): void

```js
tickerBand.destroy();
```

## CSS

Most common classes to overwrite/customize

```css
.ticker-band-widget .ticker-element {
  font-size: 11px;
  padding: 0 0.1em;
}
.ticker-band-widget .ticker-element .image {
  padding-right: 0.15em;
}
.ticker-band-widget .ticker-element .display-name {
  font-weight: bold;
}
.ticker-band-widget .ticker-element .price {
  font-size: inherit;
}
.ticker-band-widget .ticker-element .arrow {
  font-size: inherit;
}
.ticker-band-widget .ticker-element .change {
  font-size: inherit;
}
```
