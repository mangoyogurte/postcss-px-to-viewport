# postcss-px-to-viewport-with-minviewportwidth

A plugin for [PostCSS](https://github.com/postcss/postcss) that generates viewport units (vw, vh, vmin, vmax) from pixel units.

forked from [postcss-px-to-viewport](https://github.com/evrone/postcss-px-to-viewport) to add minViewportWidth pramas

### Usage

```js
{
  unitToConvert: 'px',
  viewportWidth: 1440,
  minViewportWidth: 1200,
  unitPrecision: 5,
  propList: ['*'],
  viewportUnit: 'vw',
  fontViewportUnit: 'vw',
  selectorBlackList: [],
  minPixelValue: 1,
  mediaQuery: false,
  replace: true,
  exclude: undefined,
  include: undefined,
}
```
- `unitToConvert` (String) unit to convert, by default, it is px.
- `viewportWidth` (Number) The width of the viewport.
- `minViewportWidth` (Number) The minWidth of the viewport.
- `unitPrecision` (Number) The decimal numbers to allow the vw units to grow to.
- `propList` (Array) The properties that can change from px to vw.
    - Values need to be exact matches.
    - Use wildcard * to enable all properties. Example: ['*']
    - Use * at the start or end of a word. (['*position*'] will match background-position-y)
    - Use ! to not match a property. Example: ['*', '!letter-spacing']
    - Combine the "not" prefix with the other prefixes. Example: ['*', '!font*']
- `viewportUnit` (String) Expected units.
- `fontViewportUnit` (String) Expected units for font.
- `selectorBlackList` (Array) The selectors to ignore and leave as px.
    - If value is string, it checks to see if selector contains the string.
        - `['body']` will match `.body-class`
    - If value is regexp, it checks to see if the selector matches the regexp.
        - `[/^body$/]` will match `body` but not `.body`
- `minPixelValue` (Number) Set the minimum pixel value to replace.
- `mediaQuery` (Boolean) Allow px to be converted in media queries.
- `replace` (Boolean) replaces rules containing vw instead of adding fallbacks.
- `exclude` (Regexp or Array of Regexp) Ignore some files like 'node_modules'
    - If value is regexp, will ignore the matches files.
    - If value is array, the elements of the array are regexp.
- `include` (Regexp or Array of Regexp) If `include` is set, only matching files will be converted,
  for example, only files under `src/mobile/` (`include: /\/src\/mobile\//`)
    - If the value is regexp, the matching file will be included, otherwise it will be excluded.
    - If value is array, the elements of the array are regexp.
- `landscape` (Boolean) Adds `@media (orientation: landscape)` with values converted via `landscapeWidth`.
- `landscapeUnit` (String) Expected unit for `landscape` option
- `landscapeWidth` (Number) Viewport width for landscape orientation.

> `exclude` and `include` can be set together, and the intersection of the two rules will be taken.