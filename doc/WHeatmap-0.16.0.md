# Heatmap

## New Widget

```js
var heatmap = window.fdc__widget__.WHeatmap.init(selector, initialConfig, initialLanguage, localeMessages);

var heatmap = window.fdc__widget__.WHeatmap.init('.heatmap-widget' /* optional parameters */);
```

- **selector** (_String_): Any valid querySelector
- **initialLanguage** (_String_): Language Code
- **initialConfig** (_Object_): All options can be passed here initially
  - **ric** (_Array[String]_): Exchange Symbol
  - **heatmapColors** (_Object_): Change default Heatmap colors
  - **indicator** (_String_): Change the default indicator
  - **size** (_String_): Change the default size condition
  - **sort** (_String_): Change the default sort condition
  - **sortDir** (_String_): Change the default sort direction
- **Returns** (_Object_): new widget instance

## API

### `setRic(ric)`

Set instrument code

- **ric** (_String_): Reuters Instrument Code (RIC)
- **Returns** (_void_): void

```js
heatmap.setRic('.OBX');
```

### `setColors(colorObject)`

Set the colors of the heatmap.

- **colorObject** (_Object_): The color Object has the default colors seen in the example
- **Returns** (_void_): void

```js
heatmap.setColors({
  volatilityLow: '#e6e6e6',
  volatilityHigh: '#f637a8',
  fundamentalsLow: '#b933ff',
  fundamentalsHigh: '#fe7e1a',
  changeNegative: '#a65549',
  changeNeutral: '#e6e6e6',
  changePositive: '#0489bc',
  defaultLow: '#e6e6e6',
  defaultHigh: '#0285d6'
});
/* Any subset of colors at a time is also possible. Others will keep the default. */
heatmap.setColors({
  volatilityLow: '#e6e6e6',
  volatilityHigh: '#f637a8'
});
```

### `setIndicator(fid)`

Set the indicator, presented in the first dropdown. Default is performance.

- **fid** (_String_): Field ID. Options:

  - **q.\_PCTCHNG** : performance
  - **d.\_PCTCHG_1W** : performance one week
  - **d.\_PCTCHG_1M** : performance one month
  - **d.\_PCTCHG_1Y** : performance one year
  - **d.\_VOLA_1W** : vola one week
  - **d.\_VOLA_1M** : vola one month
  - **d.\_VOLA_1Y** : vola one year
  - **q.\_ACVOL_1** : traded volume
  - **d.\_ACVOL_1W** : traded volume one week
  - **d.\_ACVOL_1M** : traded volume one month
  - **d.\_ACVOL_1Y** : traded volume one year
  - **q.\_TURNOVER** : turnover
  - **rkd.TOTALFLOAT_PCT** : free float
  - **rkd.MKTCAP** : market capitalization
  - **rkd.EPS_CHANGE_CURRY_TO_LST1Y** : earnings change to prev. year
  - **rkd.EPS_TO_PRICE** : earnings yield
  - **rkd.DPS_TO_PRICE** : dividend yield
  - **rkd.PEG** : price-earnings-growth ratio (peg)
  - **rkd.PRICE_TO_EPS_NXT1Y** : forward p/e
  - **rkd.PRICE_TO_EPS** : price / earnings ratio (p/e)
  - **rkd.PRICE_TO_BVPS** : price / book ratio (p/b)
  - **rkd.PRICE_TO_CPS** : price / cash flow ratio (p/c)
  - **rkd.PRICE_TO_NET_SALES** : price / sales ratio (p/s)

- **Returns** (_void_): void

```js
heatmap.setIndicator('q._ACVOL_1W');
```

### `setSize(fid)`

Set the condition for thq square sizes, presented in the second dropdown. Default is market capitalization.

- **fid** (_String_): Field ID. Options:

  - **equal** : All equal
  - **d.\_VOLA_1W** : volatility one week
  - **d.\_VOLA_1M** : volatility one month
  - **d.\_VOLA_1Y** : volatility one year
  - **q.\_ACVOL_1** : traded volume
  - **d.\_ACVOL_1W** : traded volume one week
  - **d.\_ACVOL_1M** : traded volume one month
  - **d.\_ACVOL_1Y** : traded volume one year
  - **q.\_TURNOVER** : turnover
  - **rkd.TOTALFLOAT_PCT** : free float
  - **rkd.MKTCAP** : market capitalization

- **Returns** (_void_): void

```js
heatmap.setIndicator('q._ACVOL_1W');
```

### `setSort(fid)`

Set the way the heatmap sorts, presented in the third dropdown. Default is performance.

- **fid** (_String_): Field ID. Options:

  - **q.\_PCTCHNG** : performance
  - **d.\_PCTCHG_1W** : performance one week
  - **d.\_PCTCHG_1M** : performance one month
  - **d.\_PCTCHG_1Y** : performance one year
  - **d.\_VOLA_1W** : vola one week
  - **d.\_VOLA_1M** : vola one month
  - **d.\_VOLA_1Y** : vola one year
  - **q.\_ACVOL_1** : traded volume
  - **d.\_ACVOL_1W** : traded volume one week
  - **d.\_ACVOL_1M** : traded volume one month
  - **d.\_ACVOL_1Y** : traded volume one year
  - **q.\_TURNOVER** : turnover
  - **rkd.TOTALFLOAT_PCT** : free float
  - **rkd.MKTCAP** : market capitalization
  - **rkd.EPS_CHANGE_CURRY_TO_LST1Y** : earnings change to prev. year
  - **rkd.EPS_TO_PRICE** : earnings yield
  - **rkd.DPS_TO_PRICE** : dividend yield
  - **rkd.PEG** : price-earnings-growth ratio (peg)
  - **rkd.PRICE_TO_EPS_NXT1Y** : forward p/e
  - **rkd.PRICE_TO_EPS** : price / earnings ratio (p/e)
  - **rkd.PRICE_TO_BVPS** : price / book ratio (p/b)
  - **rkd.PRICE_TO_CPS** : price / cash flow ratio (p/c)
  - **rkd.PRICE_TO_NET_SALES** : price / sales ratio (p/s)

- **Returns** (_void_): void

```js
heatmap.setSort('q._ACVOL_1W');
```

### `setSortDirection(direction)`

Set the direction of the sort.

- **direction** (_String_): Options: 'asc' or 'desc'. Default is 'desc'

- **Returns** (_void_): void

```js
heatmap.setSortDirection('asc');
```

### `setLocale(locale [, fallback])`

Set new locale for widget instance

- **locale** (_String_): country code
- **fallback** (_String, optional_): country code, fallback to this locale if `locale` is not found in translation strings
- **Returns** (_void_): void

```js
heatmap.setLocale('no');
```

### `getLocale()`

Get the current active locale for widget instance.

- **Returns** (_String_): country code

```js
heatmap.setLocale('no');
```

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(locale, messages)`

Add new messages to existing locale or add new locale with messages.

```js
heatmap.setLocaleMessages('en', {
  controls: {
    symbol: 'Symbol',
    placeholder: 'Enter symbol',
    indicator: 'Indicator',
    size: 'Size',
    sort: 'Sort By'
  },
  labels: {
    performance: 'Performance',
    tradeData: 'Trade Data',
    fundamentals: 'Fundamentals',
    ASC: 'ASC',
    DESC: 'DESC',
    oneWeek: 'one week',
    oneMonth: 'one month',
    oneYear: 'one year',
    vola: 'Vola',
    tradedVolume: 'Traded Volume',
    turnover: 'Turnover',
    freeFloat: 'Free Float',
    marketCap: 'Market Capitalization',
    earningsChangePrevYear: 'Earnings change to prev. year',
    earningsYield: 'Earnings Yield',
    dividendYield: 'Dividend Yield',
    PEG: 'Price-Earnings-Growth Ratio (PEG)',
    forwardPE: 'Forward P/E',
    PE: 'Price / Earnings Ratio (P/E)',
    PB: 'Price / Book Ratio (P/B)',
    PC: 'Price / Cash Flow Ratio (P/C)',
    PS: 'Price / Sales Ratio (P/S)'
  },
  short: {
    millions: 'mn',
    billions: 'bn'
  },
  messages: {
    nodata: 'No data available for this exchange. Possibly not operating at this time.',
    error: 'There was an error. We will try to get the data again in a few moments...'
  }
});
```

### `destroy()`

Destroy widget instance and remove it from DOM

- **Returns** (_void_): void

```js
heatmap.destroy();
```
