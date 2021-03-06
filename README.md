# Contribution

> 🗓 GitHub contribution streak & stat fetcher with zero dependencies

![build](https://github.com/jamieweavis/contribution/workflows/build/badge.svg)
[![Coverage](https://img.shields.io/codecov/c/github/jamieweavis/contribution.svg)](https://codecov.io/gh/jamieweavis/contribution)
[![Downloads](https://img.shields.io/npm/dt/contribution.svg)](https://npmjs.com/package/contribution)
[![Version](https://img.shields.io/npm/v/contribution.svg)](https://github.com/jamieweavis/contribution/releases)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/jamieweavis/contribution/blob/main/LICENSE.md)
[![Style](https://img.shields.io/badge/code_style-prettier-ff69b4.svg)](https://github.com/prettier/prettier)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)

- [Install](#install)
- [Usage](#usage)
- [API](#api)
  - [`fetchStats(username, [options])`](#fetchstatsusername-options)
    - [`username`](#username)
    - [`options`](#options)
      - [`onSuccess`](#onsuccess)
      - [`onFailure`](#onfailure)
      - [`enableCors`](#enablecors)
- [Related](#related)

## Install

```console
$ npm install contribution
```

## Usage

```javascript
import { fetchStats } from 'contribution';

// Callbacks
fetchStats('jamieweavis', {
  onSuccess: data => console.log(data),
  onFailure: error => console.log(error),
});

// Promises
fetchStats('jamieweavis')
  .then(data => console.log(data))
  .catch(error => console.log(error));

// Async/await
async function getContributionData() {
  try {
    const data = await fetchStats('jamieweavis');
    console.log(data);
  } catch (error) {
    console.log(error);
  }
}
```

## API

### `fetchStats(username, [options])`

Type: `Function`

Returns: `Promise`

Resolves: `Object`

Resolves an object with the following structure:

```javascript
{
  streak: {
    best: Number,
    current: Number,
  },
  contributions: {
    best: Number,
    current: Number,
    total: Number,
  }
}
```

#### `username`

Type: `String`

The GitHub username to fetch contribution data for.

#### `options`

Type: `Object`

##### `onSuccess`

Type: `Function`

Parameters: `data`

Callback function to handle the returned data. Passed a `data` object which has the same structure as the resolved data object above.

##### `onFailure`

Type: `Function`

Parameters: `error`

Callback function to handle an error. Passed an `error` object which corresponds to a HTTP Response with `error.statusCode` etc.

##### `enableCors`

Type: `Boolean`

Default: `false`

Whether to proxy the request through the [cors-anywhere](https://github.com/Rob--W/cors-anywhere) API to enable fetching data x-origin. Set this option to true if you are using `contribution` through the browser.

## Related

- [streaker](https://github.com/jamieweavis/streaker) - 🐙 GitHub contribution streak & stat tracking menu bar app
- [streaker-cli](https://github.com/jamieweavis/streaker-cli) - 🐙 GitHub contribution streak & stat tracking CLI app
