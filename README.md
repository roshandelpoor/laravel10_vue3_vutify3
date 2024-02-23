## Dependency ##
- php 8.2
- node 20
- npm 10

### _Laravel 10 - Vue 3 - vuetify_ **
- Set APP_URL in the .env file
```
APP_URL=http://127.0.0.1:8000
```

- vite.config.js
```
import { defineConfig } from "vite";
import laravel from "laravel-vite-plugin";
import vue from "@vitejs/plugin-vue";

export default defineConfig({
    plugins: [
        vue(),
        laravel({
            input: ["resources/css/app.css", "resources/js/app.js"],
            refresh: true,
        }),
    ],
});
```
- Install Vue3 and Vue-loader
```
npm install
npm install vue vue-loader
npm install @vitejs/plugin-vue
```

- Add Vue setup and create an app.vue file inside resources/js/layouts/app.vue for testing:
```
<template>
    <div>
        <h1>Hello world !!!</h1>
    </div>
</template>
```

- Navigate to resources/js/app.js and Incorporate this within app.js
```
import "./bootstrap";
import { createApp } from "vue";
import app from "./layouts/app.vue";

createApp(app).mount("#app");
```

- Update Blade resources/views/welcome.blade.php
```
<body>
    <div id="app"></div>
    @vite('resources/js/app.js')
</body>
```

- Install Vuetify3
```
npm install vuetify
```

- Inside resources/js, create vuetify.js file (resources/js/vuetify.js)and populate it with Vuetify configuration and theming options, like this:
```
// Vuetify
import "vuetify/styles";
import { createVuetify } from "vuetify";
import * as components from "vuetify/components";
import * as directives from "vuetify/directives";

const customeTheme = {
    dark: false,
    colors: {
        primary: "#673AB7",
        secondary: "#424242",
        accent: "#82B1FF",
        error: "#FF5252",
        info: "#2196F3",
        success: "#4CAF50",
        warning: "#FFC107",
        lightblue: "#14c6FF",
        yellow: "#FFCF00",
        pink: "#FF1976",
        orange: "#FF8657",
        magenta: "#C33AFC",
        darkblue: "#1E2D56",
        gray: "#909090",
        neutralgray: "#9BA6C1",
        green: "#2ED47A",
        red: "#FF5c4E",
        darkblueshade: "#308DC2",
        lightgray: "#BDBDBD",
        lightpink: "#FFCFE3",
        white: "#FFFFFF",
        muted: "#6c757d",
    },
};

const vuetify = createVuetify({
    components,
    directives,
    theme: {
        defaultTheme: "customeTheme",
        themes: {
            customeTheme,
        },
    },
});

export default vuetify;
```
- Navigate to resources/js/app.js and Modify app.js to incorporate Vuetify
```
import vuetify from "./vuetify";
createApp(app).use(vuetify).mount("#app");
```

## Testing Vuetify3 Integration ##

- Run the Servers
```
php artisan serve
npm run dev
```

- Navigate to Your App
```
http://127.0.0.1:8000
```

- Test Vuetify (Inside resources/js/layouts/app.vue)
```
<v-btn color="primary">Button</v-btn>
```

Laravel 10 integrated seamlessly with Vite, Vue3, and Vuetify3
