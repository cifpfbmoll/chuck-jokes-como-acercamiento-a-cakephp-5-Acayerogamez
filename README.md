```markdown
# API de Chistes de Chuck Norris con CakePHP

Este es un proyecto desarrollado en **CakePHP 5** como una introducción al framework. La aplicación consume la API pública de `api.chucknorris.io` para obtener un chiste aleatorio y permite al usuario guardarlo en una base de datos local **SQLite**.

## 🛠️ Tecnologías Utilizadas

*   **PHP 8.1+**
*   **CakePHP 5**
*   **Composer** para la gestión de dependencias.
*   **SQLite** como base de datos, para una configuración sencilla y sin necesidad de un servidor de base de datos.

## 🚀 Instalación Rápida

Sigue estos pasos desde tu terminal para poner en marcha el proyecto.

**1. Clona el repositorio:**
```bash
git clone https://github.com/cifpfbmoll/chuck-jokes-como-acercamiento-a-cakephp-5-Acayerogamez.git
cd chuck-jokes-como-acercamiento-a-cakephp-5-Acayerogamez
```

**2. Instala las dependencias:**
```bash
composer install
```

**3. Configura la base de datos (SQLite):**

Abre el archivo `config/app_local.php` y asegúrate de que la configuración de la base de datos (`Datasources`) apunte a un archivo SQLite dentro de tu proyecto.

```php
'Datasources' => [
    'default' => [
        'driver' => Cake\Database\Driver\Sqlite::class,
        'database' => ROOT . DS . 'tmp' . DS . 'database.sqlite', // Ruta relativa y recomendada
        'url' => env('DATABASE_URL', null),
    ],
],
```

**IMPORTANTE:** Crea el archivo de la base de datos si no existe:
```bash
touch tmp/database.sqlite
```

**4. Ejecuta las migraciones:**

Este comando creará la tabla `jokes` en tu base de datos SQLite.
```bash
php bin/cake.php migrations migrate
```

**5. Genera el Modelo:**

Usa `bake` para crear las clases del ORM (Table y Entity) para la tabla `jokes`.
```bash
php bin/cake.php bake model Jokes
```

## ▶️ Cómo Ejecutar la Aplicación

1.  **Inicia el servidor de desarrollo de PHP.** Asegúrate de apuntar a la carpeta `webroot` del proyecto.
    ```bash
    # Ejecuta este comando desde la raíz de tu proyecto
    php -S localhost:8765 -t webroot/
    ```

2.  **Abre tu navegador** y visita la siguiente URL para ver un chiste aleatorio:
    [http://localhost:8765/jokes/random](http://localhost:8765/jokes/random)

## 📖 Funcionamiento

La ruta principal `/jokes/random` está gestionada por la acción `random()` en el `JokesController.php`.

- Al cargar la página, se hace una petición a la API externa para obtener un chiste.
- El chiste se muestra en pantalla junto con un botón "Guardar".
- Al pulsar el botón, los datos del chiste se envían por POST al mismo controlador, que se encarga de validarlos y guardarlos en la base de datos SQLite.

---