# Installation
> `npm install --save @types/from2`

# Summary
This package contains type definitions for from2 (https://github.com/hughsk/from2).

# Details
Files were exported from https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/from2.
## [index.d.ts](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/from2/index.d.ts)
````ts
// Type definitions for from2 2.3
// Project: https://github.com/hughsk/from2
// Definitions by: BendingBender <https://github.com/BendingBender>
// Definitions: https://github.com/DefinitelyTyped/DefinitelyTyped

/// <reference types="node" />
import * as stream from 'stream';

export = from2;

declare function from2(read: from2.ReadInput): NodeJS.ReadableStream;
declare function from2(opts: from2.ObjectModeOptions, read: from2.ReadObjectInput): NodeJS.ReadableStream;
declare function from2(opts: from2.Options, read: from2.ReadInput): NodeJS.ReadableStream;

declare namespace from2 {
    function obj(read: ReadObjectInput): NodeJS.ReadableStream;
    function obj(opts: { objectMode?: true | undefined } & stream.ReadableOptions, read: ReadObjectInput): NodeJS.ReadableStream;

    function ctor(opts?: Options): From2Ctor<ReadInput>;
    function ctor(opts: ObjectModeOptions): From2Ctor<ReadObjectInput>;

    type ObjectModeOptions = { objectMode: true } & stream.ReadableOptions;
    type Options = { objectMode?: false | undefined } & stream.ReadableOptions;

    type From2Ctor<R extends ReadInput | ReadObjectInput> = new(read: R) => NodeJS.ReadableStream;

    type ReadObjectInput = ReadCallback<NextObjectCallback> | any[];
    type ReadInput = ReadCallback<NextCallback> | Chunk[];
    type ReadCallback<N extends NextCallback | NextObjectCallback> = (size: number, next: N) => void;
    type NextCallback = (err: any | undefined, chunk: Chunk) => void;
    type NextObjectCallback = (err: any | undefined, chunk: any) => void;
    type Chunk = string | Buffer | Uint8Array | null;
}

````

### Additional Details
 * Last updated: Tue, 06 Jul 2021 20:33:01 GMT
 * Dependencies: [@types/node](https://npmjs.com/package/@types/node)
 * Global values: none

# Credits
These definitions were written by [BendingBender](https://github.com/BendingBender).
