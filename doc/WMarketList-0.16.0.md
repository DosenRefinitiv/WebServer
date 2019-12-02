# Market List

## New Widget

```js
//var marketList = window.fdc__widgets__.WMarketList.init(selector, initialConfig, initialLanguage, localMessages);

// Example: Initialize widget with default settings
//var marketList = window.fdc__widgets__.WMarketList.init('.market-list');

// Example: Initialize widget based on a specific index
// var marketList = window.fdc__widgets__.WMarketList.init('.market-list', {
  indexRic: '.OSEBX'
});

// Example: Initialize widget based on a chain ric
// var marketList = window.fdc__widgets__.WMarketList.init('.market-list', {
  chainRic: '0#GFB.OL'
});

// Example: Initialize widget based on a custom (watch)list)
//var marketList = window.fdc__widgets__.WMarketList.init('.market-list', {
  rics: ['AKER.OL', 'BAKKA.OL', 'DNB.OL', 'ELK.OL', 'GJFS.OL', 'LSG.OL', 'NEL.OL', 'NWC.OL']
});

// Example: Initialize widget with new columns (including a custom button column)
// Note: This example uses simple 'hardcoded' strings as headerNames.
// However we recommend to use localized headerNames as shown in the example below this one.
//var marketList = window.fdc__widgets__.WMarketList.init('.market-list', {
  indexRic: '.OSEBX',
  columns: [
    {
      headerName: 'Ticker',
      field: 'x._TICKER'
    },
    {
      headerName: 'Name',
      field: 'q._DSPLY_NAME',
      minWidth: 130
    },
    {
      headerName: '',
      field: 'q.RIC',
      type: 'button',
      buttons: [
        {
          id: 'btn_01',
          label: 'Buy',
          style: 'width: 40px; height: 20px; background-color: #e0e0ff; margin: 0 1px;'
        },
        {
          id: 'btn_02',
          label: 'Sell',
          style: 'width: 40px; height: 20px; background-color: #ffe0e0; margin: 0 1px;'
        },
        {
          id: 'btn_03',
          style:
            'width: 20px; height: 20px; background-image: url("http://www.financial.com/tmp/dnb_testicon.png"); background-size: 20px 20px; border: none; margin: 0 1px;'
        }
      ],
      width: 106
    },
    {
      headerName: 'Price',
      field: 'q._TRDPRC_1',
      cellStyle: { 'background-color': '#f7f2f4' }
    },
    {
      headerName: '+/-',
      field: 'q._NETCHNG_1'
    },
    {
      headerName: '%',
      field: 'q._PCTCHNG'
    },
    {
      headerName: 'Bid',
      field: 'q._BID',
      cellStyle: { 'background-color': '#f7f2f4' }
    },
    {
      headerName: 'Bid Sz.',
      field: 'q.BIDSIZE'
    },
    {
      headerName: 'Ask',
      field: 'q._ASK',
      cellStyle: { 'background-color': '#f7f2f4' }
    },
    {
      headerName: 'Ask Sz',
      field: 'q.ASKSIZE'
    }
  ]
});

// Example: Initialize widget with new columns
// Note: In this example all headerNames point to the default localization strings (en).
// You can also provide your own localisation strings for other languages (see example below this one)
//var marketList = window.fdc__widgets__.WMarketList.init('.market-list', {
  indexRic: '.OSEBX',
  columns: [
    {
      headerName: 'i18n(custom.header.ticker)',
      field: 'x._TICKER'
    },
    {
      headerName: 'i18n(custom.header.name)',
      field: 'q._DSPLY_NAME',
      minWidth: 130
    },
    {
      headerName: 'i18n(custom.header.price)',
      field: 'q._TRDPRC_1',
      cellStyle: { 'background-color': '#f7f2f4' }
    },
    {
      headerName: 'i18n(custom.header.change)',
      field: 'q._NETCHNG_1'
    },
    {
      headerName: 'i18n(custom.header.changePercentage)',
      field: 'q._PCTCHNG'
    },
    {
      headerName: 'i18n(custom.header.bid)',
      field: 'q._BID',
      cellStyle: { 'background-color': '#f7f2f4' }
    },
    {
      headerName: 'i18n(custom.header.ask)',
      field: 'q._ASK',
      cellStyle: { 'background-color': '#f7f2f4' }
    }
  ]
});

// Example: Initialize widget providing a new language code and the corresponding translation values
// Note: In a real world example all the value strings would be real translations.
// However in this example we just prefixed the default values with "no" to symbolize a "new language".
// This example uses all available translation keys for reference

//var marketList = window.fdc__widgets__.marketList('.widgetMarketList', { indexRic: '.OSEBX' }, 'no', {
  custom: {
    header: {
      ticker: 'noTicker',
      name: 'noName',
      price: 'noPrice',
      change: 'no+/-',
      changePercentage: 'no%',
      bid: 'noBid',
      ask: 'noAsk',
      histClose: 'noHist.Close',
      time: 'noTime',
      exchange: 'noExchange',
      currency: 'noCurrency'
    }
  },
  grid: {
    page: 'noPage',
    more: 'nomore',
    to: 'noto',
    of: 'noof',
    next: 'noNext',
    last: 'noLast',
    first: 'noFirst',
    previous: 'noPrevious',
    loadingOoo: 'noLoading...',
    noRowsToShow: 'noNo Rows To Show',
    filterOoo: 'noFilter...',
    applyFilter: 'noApply Filter...',
    clearFilter: 'noClear Filter...',
    equals: 'noEquals',
    notEqual: 'noNot equal',
    lessThan: 'noLess than',
    greaterThan: 'noGreater than',
    lessThanOrEqual: 'noLess than or equal',
    greaterThanOrEqual: 'noGreater than or equal',
    inRange: 'noIn range',
    contains: 'noContains',
    notContains: 'noNot contains',
    startsWith: 'noStarts with',
    endsWith: 'noEnds with',
    andCondition: 'noAND',
    orCondition: 'noOR'
  }
});
```

- **selector** (_String_): Any valid querySelector
- **initialState** (_Object_):
  - **indexRic** (_String_): Reuters Instrument Code (RIC) for a index (e.g. ".OSEBX")
  - **columns** (_Array&lt;Object&gt;_): Array of column objects
    - **headerName** (_String_): Column header name as simple string (e.g. "Ticker") or translation key string (e.g. "i18n(custom.header.ticker)").
    - **field** (_String_): Field id (fid) (e.g. "q._NETCHNG_1")
    - **type** (_String_): The type is set dynamically and can be overwritten. This is usually only the case if you want to configure a column with custom buttons. In this case use type: 'button".
    - **buttons** (_Array&lt;Object&gt;_): Array of button objects. Only available if column type is set 'button'.
      - **label** (_String_): The label of the button
      - **class** (_String_): Custom CSS class to add to the button element
      - **style** (_String_): Custom styles for the button
      - **(any)** (_String_): You can define additional key/value pairs. You will get this key/value pairs back as payload of the clickEvent. In our examples we use 'id' to identify the button if clicked.
    - **cellClass** (_String_): Custom CSS class to add to the cells.
    - **cellStyle** (_String_): Custom styles for the cells.
    - **width** (_Float_): Initial width for the cell
    - **minWidth** (_Float_): Initial minWidth for the cell
    - **maxWidth** (_Float_): Initial maxWidth for the cell
- **initialLanguage** (_String_): Language Code (currently not used in this widget)
- **localMessages** (_Object_): Translation strings for the language code
- **Returns** (_Object_): new widget instance

## API

### `setIndexRic(ric)`

Set index during runtime.

```js
// Example: Set index after initialisation
// marketList.setIndexRic('.GDAXI');
```

- **ric** (_String_): Reuters Instrument Code (RIC)
- **Returns** (_void_): void

### `setRics(rics)`

Set a multiple rics (watchlist rows) after initialisation

```js
// Example: Set a watchlist after initialisation
marketList.setRics(['AKER.OL', 'BAKKA.OL', 'DNB.OL', 'ELK.OL', 'GJFS.OL', 'LSG.OL', 'NEL.OL', 'NWC.OL']);
```

- **rics** (_Array&lt;String&gt;_): Array of Reuters Instrument Codes (RICs)
- **Returns** (_void_): void

### `setChainRic(ric)`

Set a chain ric after initialisation

```js
// Example: Set a chain ric after initialisation
marketList.setChainRic('0#ETN.OL');
```

- **ric** (_String_): chain ric
- **Returns** (_void_): void

### `setColumns(columns)`

Set new columns after initialisation

```js
// Example: Set a watchlist after initialisation
marketList.setColumns([
  {
    headerName: 'Ticker',
    field: 'x._TICKER'
  },
  {
    headerName: 'Name',
    field: 'q._DSPLY_NAME',
    minWidth: 130
  },
  {
    headerName: 'Price',
    field: 'q._TRDPRC_1',
    cellStyle: { 'background-color': '#f7f2f4' }
  },
  {
    headerName: '+/-',
    field: 'q._NETCHNG_1'
  },
  {
    headerName: '%',
    field: 'q._PCTCHNG'
  },
  {
    headerName: 'Bid',
    field: 'q._BID',
    cellStyle: { 'background-color': '#f7f2f4' }
  },
  {
    headerName: 'Bid Sz.',
    field: 'q.BIDSIZE'
  },
  {
    headerName: 'Ask',
    field: 'q._ASK',
    cellStyle: { 'background-color': '#f7f2f4' }
  },
  {
    headerName: 'Ask Sz',
    field: 'q.ASKSIZE'
  }
]);
```

- **columns** (_Array&lt;Object&gt;_): Array of column objects
  - **headerName** (_String_): Column header name as simple string (e.g. "Ticker") or translation key string (e.g. "i18n(custom.header.ticker)").
  - **field** (_String_): Field id (fid) (e.g. "q._NETCHNG_1")
  - **type** (_String_): The type is set dynamically and can be overwritten. This is usually only the case if you want to configure a culumn with custon buttons. In this case use type: 'button".
  - **buttons** (_Array&lt;Object&gt;_): Array of button objects. Only available if column type is set 'button'.
  - **label** (_String_): The label of the button
  - **class** (_String_): Custom CSS class to add to the button element
  - **style** (_String_): Custom styles for the button
  - **(any)** (_String_): You can define additional key/value pairs. You will get this key/value pairs back as payload of the clickEvent. In our examples we use 'id' to identify the button if clicked.
  - **cellClass** (_String_): Custom CSS class to add to the cells.
  - **cellStyle** (_String_): Custom styles for the cells.
  - **width** (_Float_): Initial width for the cell
  - **minWidth** (_Float_): Initial minWidth for the cell
  - **maxWidth** (_Float_): Initial maxWidth for the cell
- **Returns** (_void_): void

### `onClick(function(event))`

Registers callback function to listen for click events

```js
// Example: Get all clicks within the grid (cellClicks, buttonClicks ...)
marketList.onClick(function callBack(event) {
  console.log('[API] onClick event from marketList. RIC: ', event.ric);
});

// Example: Handle specific clicks
marketList.onClick(function callBack(event) {
  if (event.button) {
    console.log('[API] onClick event for ric:', event.ric, 'from button:', event.button);
  } else {
    console.log(
      '[API] onClick event for ric:',
      event.ric,
      'from cell:',
      event.gridContext.colDef.field,
      'value:',
      event.gridContext.value
    );
  }
});
```

- **function** (_Function_): callBack function triggered by click event
- **event** (_Object_): Event Object
  - **ric** (_String_): Related Reuters Instrument Code (e.g. 'AAPL.OQ')
  - **origin** (_Object_): Original MouseEvent
  - **button** (_Object_): Contains the users original button configuration object for this specific button. Only available if the click source was a user configured button (i.e. configured buttons in your column configuration)
  - **gridContext** (_Object_): Contains extensive information about the grid context if the click originated from within the grid. Includes info about the clicked grid-cell, value of the cell, data of the row and many more (see example).
- **Returns** (_void_): void

### `setLocale(locale [, fallback])`

Set new locale for widget instance

```js
marketList.setLocale('no');
```

- **locale** (_String_): country code
- **fallback** (_String, optional_): country code, fallback to this locale if `locale` is not found in translation strings
- **Returns** (_void_): void

### `getLocale()`

Get the current active locale for widget instance.

```js
marketList.getLocale();
```

- **Returns** (_String_): country code

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(language, messages)`

Add new translations to existing language or add new language and translations.

```js
marketList.setLocaleMessages('no', {
  custom: {
    header: {
      ticker: 'noTicker',
      name: 'noName',
      price: 'noPrice',
      change: 'no+/-',
      changePercentage: 'no%',
      bid: 'noBid',
      ask: 'noAsk',
      histClose: 'noHist.Close',
      time: 'noTime',
      exchange: 'noExchange',
      currency: 'noCurrency'
    }
  },
  grid: {
    page: 'noPage',
    more: 'nomore',
    to: 'noto',
    of: 'noof',
    next: 'noNext',
    last: 'noLast',
    first: 'noFirst',
    previous: 'noPrevious',
    loadingOoo: 'noLoading...',
    noRowsToShow: 'noNo Rows To Show',
    filterOoo: 'noFilter...',
    applyFilter: 'noApply Filter...',
    clearFilter: 'noClear Filter...',
    equals: 'noEquals',
    notEqual: 'noNot equal',
    lessThan: 'noLess than',
    greaterThan: 'noGreater than',
    lessThanOrEqual: 'noLess than or equal',
    greaterThanOrEqual: 'noGreater than or equal',
    inRange: 'noIn range',
    contains: 'noContains',
    notContains: 'noNot contains',
    startsWith: 'noStarts with',
    endsWith: 'noEnds with',
    andCondition: 'noAND',
    orCondition: 'noOR'
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
marketList.destroy();
```

## CSS

Most common classes to overwrite/customize

Note: Several grid styles/classes can be set via configuration options.

```css
.market-list-widget {
  height: 300px;
}
```
