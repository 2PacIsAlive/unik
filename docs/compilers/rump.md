# Rumprun Unikernels

UniK uses Rumprun as a platform for compiling Go and C++ to unikernels.

---

### Golang
Compiling Go on the rumprun platform requires the following parameters be met:
* One `main` package in the root directory of your project
* All dependencies vendored with `GO15VENDOREXPERIMENT=1`

---

### Node.js
Compiling Nodejs applications on rumprun requires the following parameters be met:
* One "main" file somewhere in your project
* All dependencies already installed to `node_modules` with `npm install `
* A configuration file named `manifest.yaml` in the root directory of your project.
  * the `manifest.yaml` file should contain a single line of text like so:
    ```yaml
    main_file: YOUR_MAIN_FILE.js
    ```
    where you replace `YOUR_MAIN_FILE.js` with the relative path to your main file from the root directory of your project.

    for example, if your project has the following structure:
    ```
    $ tree myproject/
    ./myproject/
    ├── manifest.yaml
    ├── node_modules
    │   └── httpdispatcher
    │       ├── README.md
    │       ├── httpdispatcher.js
    │       ├── node_modules
    │       │   └── mime
    │       │       ├── LICENSE
    │       │       ├── README.md
    │       │       ├── build
    │       │       │   ├── build.js
    │       │       │   └── test.js
    │       │       ├── cli.js
    │       │       ├── mime.js
    │       │       ├── package.json
    │       │       └── types.json
    │       └── package.json
    └── server.js
    ```
    your `manifest.yaml` should read:
    ```yaml
    main_file: server.js
    ```
    or
    ```yaml
    main_file: ./server.js
    ```

    See [example node project](../examples/example-nodejs-app) for an example of what a Node.js project should look like.
---

### C/C++

C/C++ support coming soon!