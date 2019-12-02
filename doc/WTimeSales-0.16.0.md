# Time & Sales

## New Widget

```js
var timeSales = window.fdc__widgets__.WTimeSales.init(selector, initialConfig, initialLanguage, localMessages);

// Example: Initialize widget with default settings
var timeSales = window.fdc__widgets__.WTimeSales.init('.time-sales');

// Example: Initialize widget based on a specific ric and custom columns
var timeSales = window.fdc__widgets__.WTimeSales.init('.time-sales', {
  ric: 'AAPL.OQ',
  columns: [
    {
      headerName: 'i18n(custom.header.time)',
      field: '0'
    },
    {
      headerName: 'i18n(custom.header.price)',
      field: '6'
    },
    {
      headerName: 'i18n(custom.header.volume)',
      field: '178'
    }
  ],
  results: 10
});

// Example: Initialize widget based on a specific ric, default columns and custom time range
var timeSales = window.fdc__widgets__.WTimeSales.init('.time-sales', {
  ric: 'AAPL.OQ',
  timeRange: {
    fromDate: '2019-10-18T10:52:07',
    toDate: '2019-10-20T10:52:07'
  },
  results: 10
});
```

- **selector** (_String_): Any valid querySelector
- **initialState** (_Object_):
  - **ric** (_String_): Reuters Instrument Code (RIC) for a stock (e.g. "BMWG.DE")
  - **results** (_String_): Number of rows to fetch (default: 10)
  - **columns** (_Array&lt;Object&gt;_): Array of column objects
    - **headerName** (_String_): Column header name as simple string (e.g. "Ticker") or translation key string (e.g. "i18n(custom.header.time)").
    - **field** (_String_): ASG proxy Field id (fid) without the 'tns' prefix (e.g. "11", "178")
  - **timeRange** (_Object_):
    - **fromDate** (_String_): Starting date for the series (GMT time in yyyy-MM-dd or yyyy-MM-dd'T'HH:mm:ss)
    - **toDate** (_String_): To date for the series (GMT time in yyyy-MM-dd or yyyy-MM-dd'T'HH:mm:ss)
- **initialLanguage** (_String_): Language Code (currently not used in this widget)
- **localMessages** (_Object_): Translation strings for the language code
- **Returns** (_Object_): new widget instance

## API

### `setRic(ric)`

Set ric during runtime.

```js
// Example: Set ric after initialisation
timeSales.setRic('BMWG.DE');
```

- **ric** (_String_): Reuters Instrument Code (RIC)
- **Returns** (_void_): void

### `setColumns(columns)`

Set new columns after initialisation

```js
// Example: Set a watchlist after initialisation
timeSales.setColumns([
  {
    headerName: 'i18n(custom.header.time)',
    field: '0'
  },
  {
    headerName: 'i18n(custom.header.price)',
    field: '6'
  },
  {
    headerName: 'i18n(custom.header.volume)',
    field: '178'
  }
]);
```

- **columns** (_Array&lt;Object&gt;_): Array of column objects

  - **headerName** (_String_): Column header name as simple string (e.g. "Ticker") or translation key string (e.g. "i18n(custom.header.ticker)").
  - **field** (_String_): Field id (fid) (e.g. "q.\_NETCHNG_1")

- **Returns** (_void_): void

### `setTimeRange(timeRange)`

Set custom datetime range after initialisation

```js
// Example: Set a custom datetime range after initialisation
timeSales.setTimeRange({
  fromDate: '2019-10-18T10:52:07',
  toDate: '2019-10-20T10:52:07'
});
```

- **timeRange** (_Object_):

  - **fromDate** (_String_): Starting date for the series (GMT time in yyyy-MM-dd or yyyy-MM-dd'T'HH:mm:ss)
  - **toDate** (_String_): To date for the series (GMT time in yyyy-MM-dd or yyyy-MM-dd'T'HH:mm:ss)

- **Returns** (_void_): void

### `onClick(function(event))`

Registers callback function to listen for click events

```js
// Example: Handle 'Last trades/all trades' clicks
timeSales.onClick(function callBack(event) {
  console.log('[API] onClick event from timeSales. RIC: ' + event.ric + ' &  Action Button: ' + event.button);
});
```

- **function** (_Function_): callBack function triggered by click event
- **event** (_Object_): Event Object
  - **origin** (_Object_): Original MouseEvent
  - **ric** (_String_): Related Reuters Instrument Code (e.g. 'AAPL.OQ')
  - **button** (_Object_): Identify the button action (e.g. 'lastTrades', 'allTrades')
- **Returns** (_void_): void

### `setLocale(locale [, fallback])`

Set new locale for widget instance

```js
timeSales.setLocale('no');
```

- **locale** (_String_): country code
- **fallback** (_String, optional_): country code, fallback to this locale if `locale` is not found in translation strings
- **Returns** (_void_): void

### `getLocale()`

Get the current active locale for widget instance.

```js
timeSales.getLocale();
```

- **Returns** (_String_): country code

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(language, messages)`

Add new translations to existing language or add new language and translations.

```js
timeSales.setLocaleMessages('en', {
  custom: {
    header: {
      time: 'Time',
      ticker: 'Ticker',
      name: 'Name',
      price: 'Price',
      change: '+/-',
      changePercentage: '%',
      bid: 'Bid',
      ask: 'Ask',
      histClose: 'Hist.Close',
      volume: 'Volume'
    }
  },
  grid: {
    page: 'Page',
    more: 'more',
    to: 'to',
    of: 'of',
    next: 'Next',
    last: 'Last',
    first: 'First',
    previous: 'Previous',
    loadingOoo: 'Loading...',
    noRowsToShow: 'No Rows To Show'
  },
  messages: {
    invalidDate: 'Invalid date(s) provided.',
    futureDate: 'A future date was provided.',
    invalidFromDate: 'Start date cannot be greater than the end date.',
    nodata: 'No data available for this exchange. Probably not operating at this time.',
    error: 'There was an error. We will try to get the data again in a few moments...'
  }
});
```

- **language** (_String_): Language code
- **messages** (_Object_): Translation strings for the language code
- **Returns** (_void_): void

### `destroy()`

Destroy widget instance and remove it from DOM

- **Returns** (_void_): void

```js
timeSales.destroy();
```

## CSS

Most common classes to overwrite/customize

Note: Several grid styles/classes can be set via configuration options.

```css
.time-sales-widget {
  height: 300px;
}
```
