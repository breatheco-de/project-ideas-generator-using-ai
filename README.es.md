<!-- hide -->
# Generador de Ideas de Proyectos usando IA y React
<!-- endhide -->

<!-- howtostart -->
## 🌱 ¿Cómo iniciar este proyecto?

No clones este repositorio porque vamos a utilizar una plantilla diferente.

Recomendamos abrir la `plantilla de React` utilizando una herramienta de aprovisionamiento como [Codespaces](https://4geeks.com/lesson/what-is-github-codespaces) (recomendado) o [Gitpod](https://4geeks.com/lesson/how-to-use-gitpod). Alternativamente, puedes [clonar el repositorio de GitHub](https://4geeks.com/how-to/github-clone-repository) en tu computadora local usando el comando `git clone`.

Este es el repositorio que necesitas abrir o clonar:

```
https://github.com/4GeeksAcademy/react-hello
```

> ⚠ ¡Necesitarás tener Node.js instalado si lo haces localmente, pero todo eso ya está instalado en Codespaces o Gitpod!
<!-- endhowtostart -->

## 📝 Instrucciones

### Paso 1: Configura el Proyecto

- [ ] Configura el proyecto base desde la plantilla de React proporcionada.
  
- [ ] Sigue las instrucciones en el README del repositorio para configurar tu entorno de desarrollo.

### Paso 2: Obtén Acceso a la API de ChatGPT

- [ ] Regístrate para una cuenta en [OpenAI](https://www.openai.com/).
- [ ] Navega a la sección de API y obtén tu clave API para acceder a ChatGPT.

### Paso 3: Crea un Formulario de Entrada

- [ ] En tu aplicación React, crea un formulario donde los usuarios puedan especificar el tema o área de interés para ideas de proyectos.

### Paso 4: Conecta a la API de ChatGPT

- [ ] Utiliza la entrada del usuario para crear un prompt para la API de ChatGPT.
- [ ] Realiza una solicitud a la API de ChatGPT cuando se envíe el formulario.

Ejemplo:

```js
const handleGenerateIdeas = async (topic) => {
 const prompt = `Proporciona tres ideas de proyectos en el campo de ${topic}.`;

 try {
   const response = await fetch('https://api.openai.com/v1/engines/text-davinci-003/completions', {
     method: 'POST',
     headers: {
       'Authorization': `Bearer TU_CLAVE_API_DE_OPENAI`,
       'Content-Type': 'application/json',
     },
     body: JSON.stringify({
       prompt: prompt,
       max_tokens: 150,
       n: 1,
       stop: null,
       temperature: 0.7,
     }),
   });

   const data = await response.json();
   const generatedText = data.choices[0].text.trim();
   const ideaList = generatedText.split('\n').filter(idea => idea.trim() !== '');
   setIdeas(ideaList);
 } catch (error) {
   console.error('Error al generar ideas:', error);
 }
};
```

> **Nota:** Recuerda reemplazar `'TU_CLAVE_API_DE_OPENAI'` con tu clave API real de OpenAI.

### Paso 5: Muestra las Ideas de Proyectos Generadas

- [ ] Muestra la lista de ideas de proyectos devueltas por la API al usuario en tu aplicación React.
- [ ] Asegúrate de que las ideas se presenten en un formato legible, posiblemente con estilos para mejorar la experiencia del usuario.

### Paso 6: Bonus - Mejora la Experiencia del Usuario

- [ ] Permite a los usuarios especificar parámetros adicionales, como el número de ideas a generar o el nivel de complejidad.
- [ ] Implementa indicadores de carga mientras se procesa la solicitud a la API.
- [ ] Agrega manejo de errores para notificar a los usuarios si algo sale mal con la solicitud a la API.

### Sección de Bonus

#### Características Adicionales para Practicar y Mejorar el Proyecto

1. **Guardar Ideas:** Implementa funcionalidad para guardar o marcar como favoritas las ideas generadas para referencia futura.
2. **Compartir Ideas:** Agrega una función para compartir las ideas generadas vía correo electrónico o redes sociales.
3. **Historial:** Mantén un historial de las ideas generadas para que los usuarios puedan revisarlas sin regenerarlas.
4. **Prompts Personalizados:** Permite a usuarios avanzados ingresar sus propios prompts personalizados para la IA.
5. **Estilización:** Mejora la apariencia de la aplicación usando CSS o librerías de estilos como [Bootstrap](https://getbootstrap.com/) o [Material-UI](https://material-ui.com/).
6. **Autenticación de Usuario:** Implementa cuentas de usuario para que puedan guardar y acceder a sus ideas en diferentes dispositivos.

¡Explora diferentes mejoras para hacer tu Generador de Ideas de Proyectos más interactivo y amigable para el usuario!
