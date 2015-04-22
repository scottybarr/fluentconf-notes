# Building HTML Email That Doesn't Suck
### Litmus
* Screenshots for every mail client.

### HTML
* Stylesheets can't be used
* `<div>` can't be used.
* HTML5/CSS3 support varies
* Javascript support varies
* Image support varies

### We have to use Tables
### We have to inline CSS

### Target Outlook
* ```<!--[if mso]>```
* ```<!--[if mso12]>```

### Target webkit
* Can use media queries for responsive design. (GMail doesn't support media-queries)

### Workflow
* Hand-coding isn't maintainable or scalable.
* Modules, not pages - Dave Rupert, Paravel
* Static site generators
    - Jekyll
    - Middleman
    - Assemble
* Leverage grunt!
    - SASS/Stylus to CSS
    - Compress images `imagemin`
    - Use `premailer` gem to inline CSS
    - Images to s3
    - Generate plain text

### Responsive Email Designer
