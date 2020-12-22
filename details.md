# Details

## Adding Dependencies

- Add a line to `package.json` saying where the dependency is:

```json
{
  ...
  "dependencies": {
    ...
    "@reason-native/console": "^0.1.0"
  }
}
```

- Add a `libraries` section to the `dune` file where this depency should be available:
  - The name to use in `libraries` is the `public_name` located in that library's `dune` file: [`console.lib`](https://github.com/facebookexperimental/reason-native/blob/master/src/console/dune#L3)

```
(executable
  (name Hello)
  (public_name hello)
  (package hello)
  (libraries
    console.lib
  )
)
```

- Now `Console` is available in your source code:

```reason
Console.log("Hello again!");
```

### Dependencies from GitHub commits

- It is easy to depend on a specific commit from github:
  - _Warning: Do not do this if your library will be consumed from other places. It makes dependency resolution a headache to get correct._

```json
{
  ...
  "dependencies": {
    ...
    "@reason-native/console": "*"
  },
  "resolutions": {
    "@reason-native/console": "facebookexperimental/reason-native:console.json#a33f1528"
  }
}
```

## Recursive Sub Directories

To allow source code to be in sub-directories recursively add to the end of the `dune` file:

```
(include_subdirs unqualified)
```

Overall the file might look like:

```
(executable
  (name Hello)
  (public_name hello)
  (package hello)
)
(include_subdirs unqualified)
```

## Hide Warnings

- TODO: Explanation.

```
  (ocamlopt_flags -w -9-27)
  (ocamlc_flags -w -9-27)
```

## Printing Stack traces

- TODO: Explanation.

```
  (ocamlopt_flags -g)
  (ocamlc_flags -g)
```

```json
{
  ...
  "esy": {
    ...
    "exportedEnv": {
      "OCAMLRUNPARAM": {
        "val": "b",
        "scope": "global"
      }
    }
  }
}
```
