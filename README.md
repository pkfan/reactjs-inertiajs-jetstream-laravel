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
### STEP 5: delete all files from (resources/js) except (resources/js/bootstrap.js):
```js
[![Alt text](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh9RavNlhCe92jQvQUkCDDa9_jOola9dh8zdIxFoEHm6WTEgwKc0NkeT5qC4bsfVfwwnKqTROvEUQQYEVZUoVfG93LfKi5QoX-ljys0Mm5i4RE0ssPipb0TsAp8irwABfu3GZAeArRICq-_B2o7UU6_NUqZ-HU-KAeoP8Kv3_sd9Tus_405F2f3lOq5bAkT/s16000/reactjs%20inertia%20laravel%20jetstream%20github%201.png)]


