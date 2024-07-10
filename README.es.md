<!-- hide -->
# Crear un Generador de Excusas usando IA
<!-- endhide -->

## 🌱 ¿Cómo empezar este proyecto?

No clones este repositorio porque vamos a usar una plantilla diferente.

Recomendamos abrir la `plantilla de flask` o la `plantilla de vanilla.js` utilizando una herramienta de aprovisionamiento como [Codespaces](https://4geeks.com/es/lesson/tutorial-de-github-codespaces) (recomendado) o [Gitpod](https://4geeks.com/es/lesson/como-utilizar-gitpod). Alternativamente, puedes [clonar un repositorio de GitHub](https://4geeks.com/es/how-to/como-clonar-un-repositorio-de-github) en tu computadora local usando el comando `git clone`.

Estos son los repositorios que necesitas abrir o clonar:

```txt
🐍 Para Python:
https://github.com/4GeeksAcademy/flask-rest-hello

👩🏽‍💻 Para Javascript:
https://github.com/4GeeksAcademy/vanillajs-hello
```

> ⚠ Necesitarás tener Node.js o Python 3.7+ instalado si lo haces localmente, pero todo eso ya está instalado en Codespaces o Gitpod.

## 📝 Instrucciones

### Paso 1: Configura el Proyecto

- [ ] Elige tu lenguaje preferido y configura el proyecto boilerplate desde las plantillas proporcionadas.
   - Para Python: Usa la plantilla de Flask.
   - Para JavaScript: Usa la plantilla de VanillaJS.
   
- [ ] Sigue las instrucciones en el README de los respectivos repositorios para configurar tu entorno de desarrollo.

### Paso 2: Obtén acceso a la API de ChatGPT

- [ ] Regístrate para obtener una cuenta en [OpenAI](https://www.openai.com/).
- [ ] Navega a la sección de API y obtén tu clave API para acceder a la versión gratuita de ChatGPT.

### Paso 3: Crea un Formulario de Entrada o usa un prompt si construyes el proyecto en la terminal

- [ ] Implementa un formulario de entrada en tu lenguaje elegido donde los usuarios puedan especificar para qué debe ser la excusa.
   - Para Python (En la terminal): Puedes usar la función `prompt()` para preguntar al usuario.
   - Para JavaScript: Puedes crear un formulario HTML y manejar la sumisión del formulario con JavaScript manipulando el DOM.

### Paso 4: Conéctate a la API de ChatGPT

- [ ] Usa el valor del formulario de entrada para crear un prompt para la solicitud a la API de ChatGPT.
- [ ] Envía la solicitud a la API de ChatGPT y maneja la respuesta.

Ejemplo para Python:
```python
import requests

@app.route('/generate_excuse', methods=['POST'])
def generate_excuse():
    excuse_for = request.form['excuse_for']
    prompt = f"Dame una excusa para {excuse_for}:"
    
    response = requests.post('https://api.openai.com/v1/engines/davinci-codex/completions', 
                             headers={'Authorization': f'Bearer {api_key}'}, 
                             json={'prompt': prompt, 'max_tokens': 50})
    
    excuse = response.json()['choices'][0]['text']
    return render_template('result.html', excuse=excuse)
```

Ejemplo para JavaScript:
```javascript
document.getElementById('excuseForm').addEventListener('submit', async (event) => {
    event.preventDefault();
    const excuseFor = document.getElementById('excuseFor').value;
    const prompt = `Dame una excusa para ${excuseFor}:`;

    const response = await fetch('https://api.openai.com/v1/engines/davinci-codex/completions', {
        method: 'POST',
        headers: {
            'Authorization': `Bearer ${apiKey}`,
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({ prompt: prompt, max_tokens: 50 })
    });

    const data = await response.json();
    const excuse = data.choices[0].text;
    // Muestra la excusa al usuario
});
```

### Paso 5: Muestra la Excusa Generada

- [ ] Una vez que recibas la respuesta de la API de ChatGPT, muestra la excusa generada al usuario.
   - Para Python: Puedes mostrar la excusa en la terminal con un `print()`.
   - Para JavaScript: Puedes actualizar el DOM para mostrar la excusa.

Ejemplo para JavaScript:
```javascript
document.getElementById('excuseForm').addEventListener('submit', async (event) => {
    event.preventDefault();
    const excuseFor = document.getElementById('excuseFor').value;
    const prompt = `Dame una excusa para ${excuseFor}:`;

    const response = await fetch('https://api.openai.com/v1/engines/davinci-codex/completions', {
        method: 'POST',
        headers: {
            'Authorization': `Bearer ${apiKey}`,
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({ prompt: prompt, max_tokens: 50 })
    });

    const data = await response.json();
    const excuse = data.choices[0].text;
    document.getElementById('result').innerText = `Tu excusa es: ${excuse}`;
});
```

### Sección de Bonus

#### Características Adicionales para Practicar y Mejorar el Proyecto

1. **Estilización:** Agrega CSS para estilizar tu interfaz web, haciéndola más amigable para el usuario y visualmente atractiva.
2. **Personalización:** Permite a los usuarios especificar diferentes tipos de excusas (por ejemplo, trabajo, escuela, familia).
3. **Historial:** Almacena las excusas generadas en una base de datos o almacenamiento local para que los usuarios puedan ver las excusas generadas previamente.
4. **Manejo de Errores de API:** Agrega un manejo adecuado de errores para las solicitudes a la API para mejorar la experiencia del usuario.

¡Siéntete libre de explorar y agregar más características para hacer tu Generador de Excusas aún más robusto y amigable para el usuario!