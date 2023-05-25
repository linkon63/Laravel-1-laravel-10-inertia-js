# STEP 1: inertia installation and app.blade.php creation

# im from 2

Updated readme file ...

    s1.1-> Run command : composer require inertiajs/inertia-laravel
    

file changes form v1

    s1.2-> create app.blade.php file in views in laravel and paste this


    <!DOCTYPE html>
        <html>
        <head>
            <meta charset="utf-8" />
            <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0" />
            @vite('resources/js/app.js')
            @inertiaHead
        </head>
        <body>
            <div id="app"></div>
            @inertia
        </body>
        </html>
    s1.3: install middleware : php artisan inertia:middleware
    s1.4: 
        'web' => [
            // ...
            \App\Http\Middleware\HandleInertiaRequests::class,
            ],
    s1.5-> npm install and then npm run dev
    s1.6-> install vue js : npm install vue@latest and npm install @inertiajs/vue3
    s1.7-> vue vite plugin : npm i @vitejs/plugin-vue
    s1.8-> paste this to the app.js file and remove bootstrap 
            import { createApp, h } from 'vue'
            import { createInertiaApp } from '@inertiajs/vue3'

            createInertiaApp({
            resolve: name => {
                const pages = import.meta.glob('./Pages/**/*.vue', { eager: true })
                return pages[`./Pages/${name}.vue`]
            },
            setup({ el, App, props, plugin }) {
                createApp({ render: () => h(App, props) })
                .use(plugin)
                .mount(el)
            },
            })

    s1.9-> Create a folder in js file and here type the name you have give in route like : Test.vue 
        and route will : 
            Route::get('test', function () {
                return Inertia::render('Test');
            });
        Note: Component and file name will uppercase
        And RELOAD THE SERVER I MEAN FRONTEND SERVER