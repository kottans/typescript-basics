# TS ecosystem: architectural overview, tsconfig, ts-check, ts-ignore

## Plan

### Architectural Overview

Give short overview:
- we need to compile TS - so we have compiler, which will parse files, resolve imports, build AST, etc.
- we need separate entity for features in editor like code highlighting, autosuggestions, etc. - language service
- different consumers of TS should have a possibility to work with typescript, not only IDE and editors but developers also - `tsc` CLI

#### Links:

1. [Architectural Overview](https://github.com/microsoft/TypeScript/wiki/Architectural-Overview)
1. [tsserver](https://github.com/microsoft/TypeScript/wiki/Standalone-Server-%28tsserver%29)
1. Flow language server is somewhere inside of its [core](https://github.com/facebook/flow)
1. Both TS and Flow use [language server protocol](https://github.com/Microsoft/language-server-protocol/)

### tsconfig

- Tell in human language part from TS doc
- Tell about `jsconfig`
- One word about featueres of VSCode and `tsconfig`

#### Links
1. https://www.typescriptlang.org/docs/handbook/tsconfig-json.html
1. https://code.visualstudio.com/docs/languages/jsconfig
1. https://code.visualstudio.com/docs/typescript/typescript-tutorial#_tsconfigjson

### ts-check, ts-ignore, etc.

Just tell about them and show examples


