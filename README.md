# package-json-types

Type definitions if you want to use the content of a _package.json_ file
in TypeScript, e.g. through a `require` call or if you load such payload
from other sources.

Based on the documentation of [npm](https://docs.npmjs.com/files/package.json)
and [yarn](https://classic.yarnpkg.com/en/docs/package-json/) and a few
observed real world examples to see what's out there and could be standard.

## Usage

Simply import this typings-only package and then access the members, but note
that pretty much everything can be missing or in a wrong format, unless you
deal with your own content and know what to expect:

    import * as packageJson from "package-json-types";

    const pkg = {} as unknown as packageJson.Body;

    console.log("version number is", pkg.version);

    if (!!pkg.private) {
        console.log("package is private");
    }

    const author = pkg.author as packageJson.HasName;
    console.log("made by:", author.name);

To facilitate things there are a few subtypes, and also some fields of Yarn and
TypeScript additions supported. For details just have a look the typings directly.

Note that most things in _package.json_ are optional, so often you need to check
for a field's existence, type and integrity. Unless it's your own and you know
that to expect.

## Contribution

Something broken? Anything missing? Ideas for additional types?

Please contact me, or better submit a pull request. Thank you!
