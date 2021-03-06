---
title: "Known Issues"
redirect_from:
  - /guides/KNOWN-ISSUES
  - /guides/knownissues
  - /guides/knownIssues
---

- ~~ts-jest: some wierd behavior on ts-jest (only) leads to type errors~~ got fixed in `ts-jest 24.1.0` / `jest 24.9.0`
- ts-node: never run `ts-node --transpile-only` (seems like ts-node will not fix it)
- typegoose dosnt work with classes that have the same name [{% include gitissue repo="typegoose" num=23 %}, {% include gitissue repo="typegoose" num=24 %}]
- `@prop` cannot be applied to `get` & `set` (virtuals), because virtuals do not accept options & schema.loadClass wouldnt load these
- please make sure to use the right decorator execution order to prevent something like hook to fail if `@modelOptions` changes the name, [here is a reference](https://github.com/wycats/javascript-decorators/issues/29), [another reference](https://stackoverflow.com/a/50714345/8944059)
- typescript provide the option to alias paths (with `tsconfig-paths`), but is somehow incompatible with typegoose, [more info in here](https://github.com/szokodiakos/typegoose/issues/392)
- Self-Containing Classes do not work currently (Maximum Class Stack Size Exceeded)
- Multi-Dimensional Arrays are currently just an `Array` that allows **any** type, for now, trust typescript on this one [{% include gitissue repo="typegoose" num=65 %}]
- Generic Properties wont work, without specifing what type it will be (otherwise typescript will compile it to "Object" and mongoose translates it to "Mixed")
- Typegoose (/ Mongoose) currently dosnt work well with `class-transformer`, when you want to get a POJO, use `model.operation.lean()` OR `doc.toJSON()` - but `classToPlain` (or any other method from CT) will not work and map incorrect properties (More info: {% include gitissue repo="typegoose" num=61 %}, [typegoose#9 (comment)](https://github.com/typegoose/typegoose/issues/96#issuecomment-549031131), [class-transformer#227](https://github.com/typestack/class-transformer/issues/227))
- when `@prop` is used on `public _id: any`, it will error out - this is intendet mongoose behaviour

[Please look here first, to decide if it is an typegoose/mongoose issue](https://github.com/Automattic/mongoose/issues?utf8=✓&q=is%3Aissue+involves%3Ahasezoey)
