# reactjs inertiajs jetstream laravel
replace vuejs with reactjs with jetsream laravel setup. So you can use and create inertiajs laravel app with reactjs

### STEP 1: create laravel app and install jetstream
```bash
composer create-project laravel/laravel example-app

cd example-app

composer require laravel/jetstream
```

### STEP 2: Install Jetstream With Inertia 
```bash
php artisan jetstream:install inertia
```

### STEP 3: replace (package.json) with following.
```json
{
    "private": true,
    "type": "module",
    "scripts": {
        "dev": "vite",
        "build": "vite build"
    },
    "devDependencies": {
        "@inertiajs/react": "^1.0.14",
        "@tailwindcss/forms": "^0.5.2",
        "@tailwindcss/typography": "^0.5.2",
        "@vitejs/plugin-react": "^4.2.1",
        "autoprefixer": "^10.4.7",
        "axios": "^1.6.1",
        "laravel-vite-plugin": "^0.8.0",
        "postcss": "^8.4.14",
        "tailwindcss": "^3.1.0",
        "vite": "^4.0.0"
    },
    "dependencies": {
        "react": "^18.2.0",
        "react-dom": "^18.2.0"
    }
}

```

### STEP 4: replace (vite.config.js) with following:
```js
import { defineConfig } from 'vite'
import laravel from 'laravel-vite-plugin';
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [
    laravel({
        input: 'resources/js/app.jsx',
        refresh: true,
    }),
    react()],
})
```
### STEP 5: install all dependencies :
```js
npm install
```

### STEP 6: delete all files from (resources/js) except (resources/js/bootstrap.js):
[![Alt text](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh9RavNlhCe92jQvQUkCDDa9_jOola9dh8zdIxFoEHm6WTEgwKc0NkeT5qC4bsfVfwwnKqTROvEUQQYEVZUoVfG93LfKi5QoX-ljys0Mm5i4RE0ssPipb0TsAp8irwABfu3GZAeArRICq-_B2o7UU6_NUqZ-HU-KAeoP8Kv3_sd9Tus_405F2f3lOq5bAkT/s16000/reactjs%20inertia%20laravel%20jetstream%20github%201.png)]

### STEP 7: create file (resources/js/app.jsx) and add following code:
```jsx
import "./bootstrap";

import { resolvePageComponent } from "laravel-vite-plugin/inertia-helpers";
import { createInertiaApp } from "@inertiajs/react";
import { createRoot } from "react-dom/client";


createInertiaApp({
    resolve: (name) =>
        resolvePageComponent(
            `./Pages/${name}.jsx`,
            import.meta.glob("./Pages/**/*.jsx")
        ),

    setup({ el, App, props, plugin }) {
        createRoot(el)
            .render(<App {...props} />);
    },

    progress: {
        color: "#4B5563",
    },
});

```

### STEP 8: create file (resources/js/Pages/Welcome.jsx) and add following code:
```jsx
import { Head } from '@inertiajs/react'

export default function Welcome() {
  return (
    <>
      <Head title="Welcome" />
      <h1>Welcome</h1>
      <p>Hello welcome to your first  <span style={{color:'green'}}>react-Inertia</span> and <span style={{color:'red'}}>jetstream laravel</span> app!</p>

      <a href='https://www.linkedin.com/in/pkfan/'>created by pkfan [linkedin] </a>
    </>
  )
}

```

### STEP 9: replace file (resources/views/app.blade.php) with following code:
```html
<!DOCTYPE html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">

        <title inertia>{{ config('app.name', 'Laravel') }}</title>

        <!-- Fonts -->
        <link rel="preconnect" href="https://fonts.bunny.net">
        <link href="https://fonts.bunny.net/css?family=figtree:400,500,600&display=swap" rel="stylesheet" />

        <!-- Scripts -->
        @routes
        @viteReactRefresh
        @vite(['resources/js/app.jsx', "resources/js/Pages/{$page['component']}.jsx"])
        @inertiaHead
    </head>
    <body class="font-sans antialiased">
        @inertia
    </body>
</html>

```

### STEP 2: finally run following command to start work on your project
```bash
npm run dev
OR
npm run build
```

you can check all jetstream link from (.vue) js files and then use those links in reactjs
```
e.g. 
  1) route.get('login',data)
  2) <Link href='login' />

  use these links in react to handle all jetstream (fortify) auth
```






