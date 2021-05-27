
[![forthebadge](https://forthebadge.com/images/badges/open-source.svg)](https://forthebadge.com)
[![forthebadge](https://forthebadge.com/images/badges/built-with-love.svg)](https://forthebadge.com)

# <img src="https://wren.io/wren.svg" valign="middle" width="100"> wren-package

![MIT licensed](https://badgen.net/badge/license/MIT/cyan?scale=1.2)
![wren 0.4](https://badgen.net/badge/wren/0.4/blue?scale=1.2)
![experimental](https://badgen.net/badge/experimental/yes/red?scale=1.2)
![wren-console](https://badgen.net/badge/wren-console/yes/green?scale=1.2)
![wren-cli](https://badgen.net/badge/wren-cli/no/red?scale=1.2)

<!-- ![version alpha](https://badgen.net/badge/version/alpha/orange?scale=1.5) -->



Dirt simple package management/dependencies for [Wren Console](https://github.com/joshgoebel/wren-console) projects.

### What it looks like

```js
import "wren-package/package" for WrenPackage, Depencency

class Package is WrenPackage {
  construct new() {}
  name { "wren-test-runner" }
  dependencies {
    return [
      Depencency.new("wren-testie", "0.1.0", "https://github.com/joshgoebel/wren-testie.git")
    ]
  }
}

Package.new().default()
```

### Installation

First you'll need to install `wren-package` itself to your "global" `wren_modules` (likely in `HOME` directory).  After that any project under `HOME` will be able to import `wren-package` without issue.

```
cd ~
mkdir -p wren_modules
cd wren_modules
git clone https://github.com/joshgoebel/wren-package.git
```

### How it Works

Run it to get a list of what the package contains:

- `wrenc package.wren`

```
Usage:
./package.wren install

wren-test-runner dependencies:
- wren-testie 0.1.0
```

Or ask it install everything:

- `wrenc package.wren install`

```
 - installing wren-testie 0.1.0
 - [R] git clone -q https://github.com/joshgoebel/wren-testie.git wren_modules/wren-testie
 - [R] git checkout --detach 0.1.0
HEAD is now at 921b912 show variety
 * 1 dependency(s). All good.
```

### FAQ

**What prevents this from working with Wren CLI?**

Off the top of my head the official Wren CLI doesn't currently support:

- `Process.exit` (PR open, needs work)
- `Process.exec` (PR open)

### Contributions

Licensed MIT and open to contributions!

Please open an issue to discuss or find me on [Wren Discord](https://discord.gg/VTzuWmBavH).
