# Trends

## New Widget

```js
var trends = window.fdc__widgets__.WTrends.init(selector, initialConfig, initialLanguage, localeMessages);

var trends = window.fdc__widgets__.WTrends.init('.trends-widget');
```

- **selector** (_String_): Any valid querySelector
- **initialConfig** (_Object_):
  - **ric** (_String_): RIC (Reuters Instrument Codes)
- **initialLanguage** (_String_): Language Code (currently not used in this widget)
- **localMessages** (_Object_): Translation strings for the language code
- **Returns** (_Object_): new widget instance

## API

### `setRic(ric)`

Set the RIC for the Trend

- **ric** (_String_): RIC (Reuters Instrument Codes)
- **Returns** (_void_): void

```js
trends.setRic('.GDAXI');
```

### `setLocale(locale [, fallback])`

Set new locale for widget instance

- **locale** (_String_): country code
- **fallback** (_String, optional_): country code, fallback to this locale if `locale` is not found in translation strings
- **Returns** (_void_): void

```js
trends.setLocale('no');
```

### `getLocale()`

Get the current active locale for widget instance.

- **Returns** (_String_): country code

```js
var countryCode = trends.getLocale();
```

### `getLocaleMessages(locale)`

Get the message keys and values for the given locale.

- **locale** (_String_): country code
- **Returns** (_Object_): locale messages

### `setLocaleMessages(locale, messages)`

Add new messages to existing locale or add new locale with messages.

```js
trends.setLocaleMessages('no', {
  progressBar: {
    advancers: 'Ned',
    decliners: 'Opp',
    unchanged: 'Ued'
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
trends.destroy();
```
