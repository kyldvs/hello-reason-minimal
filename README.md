# hello-reason-minimal

Minimal setup for running Reason code.

## Install `esy`

Globally install [`esy`](https://www.npmjs.com/package/esy) so that the `esy`
command is available in the terminal.

```
npm install -g esy
```

_This may be useful: [Global npm without sudo](https://github.com/sindresorhus/guides/blob/master/npm-global-without-sudo.md)_

## Clone this repo

```bash
git clone https://github.com/kyldvs/hello-reason-minimal
cd hello-reason-minimal
```

## Install the dependencies and build

```bash
esy
```

_This is a combination of `esy install` and `esy build`_

## Execute `Hello.re`

```bash
esy x hello
```

_This will automatically rebuild if there are changes_

## VSCode Support

- Install the [OCaml Platform](https://marketplace.visualstudio.com/items?itemName=ocamllabs.ocaml-platform) extension.
- Create `.vscode/settings.json` in this repo:

```json
{
  "ocaml.sandbox": {
    "kind": "esy",
    "root": "/path/to/hello-reason-minimal"
  }
}
```

- Relaunch VSCode

## More Details

- For some more details and additional setup see: [`details.md`](details.md)
