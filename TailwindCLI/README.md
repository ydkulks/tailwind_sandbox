# TailwindCLI

Installing TailwindCLI in Node.js application

TailwindCLI requires CSS as input and returns a CSS file that can be used to
style the webpages by importing the file that TailwindCLI has created as output

## Example file structure

```terminal
┠─ public
┃  ┠─ index.html
┃  ┠─ script.js
┃  ┠─ output.css
┠─ src
┃  ┠─ input.css
┠─ tailwind.config.js
┠─ index.js
```

## Step 1 : Install Tailwind CSS

```bash
npm install -D tailwindcss
npx tailwindcss init
```

## Step 2 : Configure your template paths

Add paths to where the CSS files need to be generated.

This is the example code provided in official doc.

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

In this case, it would be like the following

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./public/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

## Step 3 : Add Tailwind directives to your CSS

`src/input.css`

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## Step 4 : Start Tailwind build process

Run the following command in terminal

```bash
npx tailwindcss -i ./src/input.css -o ./public/output.css --watch
```

Or add this command in your `package.json` file

```json
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node index.js && npx tailwindcss -i ./src/input.css -o ./public/output.css --watch",
    "dev": "node index.js",
    "tailwind":"npx tailwindcss -i ./src/input.css -o ./public/output.css --watch"
  },
```

## Step 5 : Start using Tailwind in your HTML

Add your compiled CSS file to the `<head>` and start using Tailwind’s utility
classes to style your content.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link href="output.css" rel="stylesheet" />
  </head>
  <body>
    <h1 class="text-3xl font-bold underline">Hello world!</h1>
  </body>
</html>
```
