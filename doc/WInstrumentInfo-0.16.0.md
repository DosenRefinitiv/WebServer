# Instrument Info

## New Widget

```js
var instrumentInfo = window.fdc__widget__.WInstrumentInfo.init(
  selector,
  initialConfig,
  initialLanguage,
  localeMessages
);

var instrumentInfo = window.fdc__widget__.WInstrumentInfo.init('.instrument-info-widget', 'en', {
  truncateNames: true
});
```

- **selector** (_String_): Any valid querySelector
- **initialLanguage** (_String_): Language Code
- **initialState** (_Object_):
  - **ric** (_String_): RIC (Reuters Instrument Codes)
  - **columns** (_Array&lt;Object&gt;_): Array of column objects
    - **headerName** (_String_): Column header name as simple string (e.g. "Bid") or translation key string (e.g. "custom.header.bid").
    - **field** (_String_): Field id (fid) (e.g. "q.\_NETCHNG_1")
  - **truncateNames** (_Boolean_): Truncates longer display names
  - **buttons** (_Array_): Array of button objects
    - **label** (_String_): The label of the button
    - **class** (_String_): Custom CSS class to add to the button element
    - **style** (_String_): Custom styles for the button
    - **(any)** (_String_): You can define additional key/value pairs. You will get this key/value pairs back as payload of the clickEvent. In our examples we use 'id' and 'label' to identify
- **Returns** (_Object_): new widget instance

## API

### `setRic(ric)`

Set instrument codes to change ticker content

- **ric** (_String_): Reuters Instrument Code (RIC)
- **Returns** (_void_): void

```js
instrumentInfo.setRic('AKER.OL');
```

### `setColumns(columns)`

Set new columns after initialisation

```js
// Example: Set a watchlist after initialisation
instrumentInfo.setColumns([
  {
    headerName: 'bid',
    field: 'q._BID'
  },
  {
    headerName: 'bidsize',
    field: 'q.BIDSIZE'
  },
  {
    headerName: 'seller',
    field: 'q._ASK'
  },
  {
    headerName: 'asksize',
    field: 'q.ASKSIZE'
  },
  {
    headerName: 'end',
    field: 'q._HST_CLOSE'
  },
  {
    headerName: 'opening',
    field: 'q._OPEN_PRC'
  },
  {
    headerName: 'high',
    field: 'q._HIGH_1'
  },
  {
    headerName: 'low',
    field: 'q._LOW_1'
  },
  {
    headerName: 'totvol',
    field: 'q._ACVOL_1'
  },
  {
    headerName: 'currency',
    field: 'x._CURRENCY'
  },
  {
    headerName: 'time',
    field: 'q._TRDTIM_1'
  },
  {
    headerName: 'roundlot',
    field: 'q.LOT_SIZE'
  }
]);
```

- **columns** (_Array&lt;Object&gt;_): Array of column objects
  - **headerName** (_String_): Column header name as simple string (e.g. "Bid" or "bid" case insensitive)
  - **field** (_String_): Field id (fid) (e.g. "q.\_BID")
- **Returns** (_void_): void

### `setButtons(buttons)`

Set new columns after initialisation

```js
// Example: Set a watchlist after initialisation
instrumentInfo.setButtons([
  {
    id: 'btn_01',
    label: 'X01',
    style: 'background-color: #4f6b06; color:#fff;border:1px solid #4d5210;'
  },
  {
    id: 'btn_02',
    label: 'X02',
    class: 'btn-info'
  },
  {
    id: 'btn_03',
    label: 'X03',
    style: 'background-color: #90589c; color:#fff;border:1px solid #5d1577;'
  }
]);
```

- **buttons** (_Array&lt;Object&gt;_): Array of column objects
  - **id** (_String_): A custom unique ID (e.g. "X01", "X02")
  - **label** (_String_): The label of the button
  - **class** (_String_): Custom CSS class to add to the button element
  - **style** (_String_): Custom styles for the button
- **Returns** (_void_): void

### `onClick(function(event))`

Registers callback function to listen for click events

- **function** (_Function_): callBack function triggered by click event
- **event** (_Object_): Event Object
  - **origin** (_Object_): Original Event
  - **ric** (_String_): Reuters Instrument Code (e.g. 'AAPL.OQ')
- **Returns** (_void_): void

```js
instrumentInfo.onClick(function callBack(event) {
  console.log('[API] onClick event from instrumentInfo. RIC: ', event.data.ric);
});
```

### `setLocale(locale [, fallback])`

Set new locale for widget instance

- **locale** (_String_): country code
- **fallback** (_String, optional_): country code, fallback to this locale if `locale` is not found in translation strings
- **Returns** (_void_): void

```js
instrumentInfo.setLocale('no');
```

### `getLocale()`

Get the current active locale for widget instance.

- **Returns** (_String_): country code

```js
var countryCode = instrumentInfo.getLocale();
```

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(locale, messages)`

Add new messages to existing locale or add new locale with messages.

```js
instrumentInfo.setLocaleMessages('en', {
  custom: {
    header: {
      high: 'High',
      low: 'Low',
      currency: 'Currency',
      opening: 'Open',
      end: 'End',
      totvol: 'Tot.vol.',
      time: 'Time',
      buyer: 'Bid',
      seller: 'Ask',
      bid: 'Bid',
      ask: 'Ask',
      bidsize: 'Bid Size',
      asksize: 'Ask Size',
      roundlot: 'Lot Size'
    }
  },
  button: {
    list: 'List',
    buy: 'Buy',
    sell: 'Sell',
    viewcompanypage: 'View Company Page'
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
instrumentInfo.destroy();
```
