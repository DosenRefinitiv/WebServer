# Market Tiles

## New Widget

```js
var marketTiles = window.fdc__widgets__.WMarketTiles.init(selector, initialConfig, initialLanguage, localMessages);

// Example: Initialize widget with default settings
var marketTiles = window.fdc__widgets__.WMarketTiles.init('.market-tiles');

// Example: Initialize widget based on a specific index
var marketTiles = window.fdc__widgets__.WMarketTiles.init('.market-tiles', {
  indexRic: '.OSEBX'
});

// Example: Initialize widget based on a chain ric
var marketTiles = window.fdc__widgets__.WMarketTiles.init('.market-tiles', {
  chainRic: '0#GFB.OL'
});

// Example: Initialize widget based on a custom (watch)list)
var marketTiles = window.fdc__widgets__.WMarketTiles.init('.market-tiles', {
  rics: ['AKER.OL', 'BAKKA.OL', 'DNB.OL', 'ELK.OL', 'GJFS.OL', 'LSG.OL', 'NEL.OL', 'NWC.OL']
});

// Example: Initialize widget providing a new language code and the corresponding translation values
// Note: In a real world example all the value strings would be real translations.
// However in this example we just prefixed the default values with "no" to symbolize a "new language".
// This example uses all available translation keys for reference

var marketTiles = window.fdc__widgets__.WMarketTiles.init('.widgetMarketList', { indexRic: '.OSEBX' }, 'no', {
  quoteView: {
    price: 'noPRICE',
    changePercentage: 'noPERFORMANCE %',
    change: 'noPERFORMANCE',
    volume: 'noVOLUME',
    open: 'noOPEN',
    high: 'noHIGH',
    low: 'noLOW'
  }
});
```

- **selector** (_String_): Any valid querySelector
- **initialState** (_Object_):
  - **indexRic** (_String_): Reuters Instrument Code (RIC) for a index (e.g. ".OSEBX").
  - **rics** (_Array_): Array of Reuters Instrument Codes (RICs). Note: You can only set indexRic _or_ rics. If both are provided then indexRic will supercede.
- **initialLanguage** (_String_): Language Code (currently not used in this widget)
- **localMessages** (_Object_): Translation strings for the language code
- **Returns** (_Object_): new widget instance

## API

### `setIndexRic(ric)`

Set index during runtime.

```js
// Example: Set index after initialisation
marketTiles.setIndexRic('.SPX');
```

- **ric** (_String_): Reuters Instrument Code (RIC)
- **Returns** (_void_): void

### `setRics(rics)`

Set a multiple rics (watchlist rows) after initialisation

```js
// Example: Set a watchlist after initialisation
marketTiles.setRics(['AKER.OL', 'BAKKA.OL', 'DNB.OL', 'ELK.OL', 'GJFS.OL', 'LSG.OL', 'NEL.OL', 'NWC.OL']);
```

- **rics** (_Array&lt;String&gt;_): Array of Reuters Instrument Codes (RICs)
- **Returns** (_void_): void

### `setChainRic(ric)`

Set a chain ric after initialisation

```js
// Example: Set a chain ric after initialisation
marketTiles.setChainRic('0#ETN.OL');
```

- **ric** (_String_): chain ric
- **Returns** (_void_): void

### `onClick(function(event))`

Registers callback function to listen for click events

```js
// Example: Get click events
marketTiles.onClick(function callBack(event) {
  console.log('[API] onClick event from marketTiles. RIC: ', event.ric);
});
```

- **function** (_Function_): callBack function triggered by click event
- **event** (_Object_): Event Object
  - **ric** (_String_): Related Reuters Instrument Code (e.g. 'AAPL.OQ')
  - **origin** (_Object_): Original MouseEvent
- **Returns** (_void_): void

### `setLocale(locale [, fallback])`

Set new locale for widget instance

```js
marketTiles.setLocale('no');
```

- **locale** (_String_): country code
- **fallback** (_String, optional_): country code, fallback to this locale if `locale` is not found in translation strings
- **Returns** (_void_): void

### `getLocale()`

Get the current active locale for widget instance.

```js
marketTiles.getLocale();
```

- **Returns** (_String_): country code

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(language, messages)`

Add new translations to existing language or add new language and translations.

```js
marketTiles.setLocaleMessages('no', {
  quoteView: {
    price: 'PRICE',
    changePercentage: 'PERFORMANCE %',
    change: 'PERFORMANCE',
    volume: 'VOLUME',
    open: 'OPEN',
    high: 'HIGH',
    low: 'LOW'
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
marketTiles.destroy();
```

## CSS

Most common classes to overwrite/customize

```css
.market-tiles-widget {
  height: 300px;
}
.market-tiles-widget .tile-element {
  cursor: pointer;
}
.market-tiles-widget .tile-element .flag {
  //
}
.market-tiles-widget .tile-element .display-name {
  //
}
.market-tiles-widget .tile-element .trade-date {
  //
}
.market-tiles-widget .tile-element .trade-date {
  //
}
.market-tiles-widget .tile-element .price .label {
  //
}
.market-tiles-widget .tile-element .price .value {
  //
}
.market-tiles-widget .tile-element .perf-percentage .label {
  //
}
.market-tiles-widget .tile-element .perf-percentage .value {
  //
}
.market-tiles-widget .tile-element .perf-abs .label {
  //
}
.market-tiles-widget .tile-element .perf-abs .value {
  //
}
.market-tiles-widget .tile-element .volume .label {
  //
}
.market-tiles-widget .tile-element .volume .value {
  //
}
.market-tiles-widget .tile-element .open .label {
  //
}
.market-tiles-widget .tile-element .open .value {
  //
}
.market-tiles-widget .tile-element .high .label {
  //
}
.market-tiles-widget .tile-element .high .value {
  //
}
.market-tiles-widget .tile-element .low .label {
  //
}
.market-tiles-widget .tile-element .low .value {
  //
}
```
