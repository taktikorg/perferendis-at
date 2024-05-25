# @taktikorg/perferendis-at <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

Define a data property on an object. Will fall back to assignment in an engine without descriptors.

The three `non*` argument can also be passed `null`, which will use the existing state if available.

The `loose` argument will mean that if you attempt to set a non-normal data property, in an environment without descriptor support, it will fall back to normal assignment.

## Usage

```javascript
var defineDataProperty = require('@taktikorg/perferendis-at');
var assert = require('assert');

var obj = {};
defineDataProperty(obj, 'key', 'value');
defineDataProperty(
	obj,
	'key2',
	'value',
	true, // nonEnumerable, optional
	false, // nonWritable, optional
	true, // nonConfigurable, optional
	false // loose, optional
);

assert.deepEqual(
	Object.getOwnPropertyDescriptors(obj),
	{
		key: {
			configurable: true,
			enumerable: true,
			value: 'value',
			writable: true,
		},
		key2: {
			configurable: false,
			enumerable: false,
			value: 'value',
			writable: true,
		},
	}
);
```

[package-url]: https://npmjs.org/package/@taktikorg/perferendis-at
[npm-version-svg]: https://versionbadg.es/ljharb/@taktikorg/perferendis-at.svg
[deps-svg]: https://david-dm.org/ljharb/@taktikorg/perferendis-at.svg
[deps-url]: https://david-dm.org/ljharb/@taktikorg/perferendis-at
[dev-deps-svg]: https://david-dm.org/ljharb/@taktikorg/perferendis-at/dev-status.svg
[dev-deps-url]: https://david-dm.org/ljharb/@taktikorg/perferendis-at#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@taktikorg/perferendis-at.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@taktikorg/perferendis-at.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@taktikorg/perferendis-at.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@taktikorg/perferendis-at
[codecov-image]: https://codecov.io/gh/ljharb/@taktikorg/perferendis-at/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/ljharb/@taktikorg/perferendis-at/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/ljharb/@taktikorg/perferendis-at
[actions-url]: https://github.com/taktikorg/perferendis-at/actions
