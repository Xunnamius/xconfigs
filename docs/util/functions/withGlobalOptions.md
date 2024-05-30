[**@-xun/configs**](../../README.md) • **Docs**

***

[@-xun/configs](../../README.md) / [util](../README.md) / withGlobalOptions

# Function: withGlobalOptions()

> **withGlobalOptions**\<`CustomCliArguments`\>(`customBuilder`?, `hasVersion`?): `Promise`\<[`WithGlobalOptionsReturnType`](../type-aliases/WithGlobalOptionsReturnType.md)\<`CustomCliArguments`\>\>

Returns a builder function (alongside a live data context) that wraps
`customBuilder` to provide standard CLI options (i.e. silent, etc). Most if
not all commands should wrap their builder objects/functions with this
function.

This function enables three additional optionals-related units of
functionality:

1. Implements https://github.com/yargs/yargs/issues/2392 via analysis of the
   returned options object to perform mutual exclusivity checks per
   exclusivity group (represented by `conflicts`). That is: providing `{
   demandOption: true, conflicts: ['x', 'y'] }` for both the `x` and `y`
   commands (including hyphens) will trigger a check to ensure exactly one of
   those two options was given. Commands that are listed as conflicts in one
   command but not the other are allowed.

2. Providing `{ demandOption: ['x', 'y'] }` for both the `x` and `y` commands
   (including hyphens) will trigger a check to ensure at least one of those
   two options was given. Providing such a value for `demandOption` on one
   command but not the other will result in an assertion failure.

3. Handles command grouping automatically. However, not that this function
   handles command grouping for you **only if you return an options object**
   and **only if you add options via said options object**. Specifically:
   calling `blackFlag.options(...)` within `customBuilder` will cause
   undefined behavior.

## Type parameters

• **CustomCliArguments** *extends* [`GlobalCliArguments`](../type-aliases/GlobalCliArguments.md)

## Parameters

• **customBuilder?**: [`ExtendedBuilderObject`](../type-aliases/ExtendedBuilderObject.md) \| (...`args`) => [`ExtendedBuilderObject`](../type-aliases/ExtendedBuilderObject.md)

• **hasVersion?**: `boolean`= `false`

## Returns

`Promise`\<[`WithGlobalOptionsReturnType`](../type-aliases/WithGlobalOptionsReturnType.md)\<`CustomCliArguments`\>\>

## Source

[src/util.ts:154](https://github.com/Xunnamius/xconfigs/blob/7129e155987055d658c285b3a31d449ff5e71ba7/src/util.ts#L154)
