# Eliminate JS Code Smells
### Copy/Paste Smell
* jsinspect -> Detects copy/paste smells
* jscpd -> Works across JS/TypeScript/CSS/SCSS/HTML
* Can set the rules to be less granular (don't match single lines)

### Switch Statement Smell
* Violates the open/closed principals from SOLID
* Adding more code to a switch statement means changing perfectly fine code.
* es-lint:
    - `no-switch`
    - `no-complex-switch-case`


### Magic Strings
* Use ES6 constants/symbols, don't force strings into your code.

### Make use of eslint-disable
* Limit it to certain rules:
    - `/* eslint-disable no-switch */`

### The This Abyss Smell
* Avoid `var that = this;`
* Use `.bind(this)` with IE8 shim.
* Use ES6 Fat arrow
* Use functional programming `this.teeth.forEach(this.clean.bind(this));` // Looks like a smell IMO
* Helpful ESLint rules:
    - `no-this-assign`
    - `consistent-this`
    - `no-extra-bind`

### Crisp Concatenation Smell
* `@thomasfuchs` string interpolation
* ES6 String Templates
* `no-complex-string-concatenation`

### Inappropriate Intimacy Smell
* Remove tightly coupled dependencies
* Could be resolved with DI or a message broker.

### Additional ESLint Plugins
* `eslint-plugin-react`
* `eslint-plugin-angular`
