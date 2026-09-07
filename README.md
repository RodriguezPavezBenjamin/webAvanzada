Integrantes: Alvaro Del Pino y  Benjamin Rodriguez Pavez


Pregunta 1
**¿Por qué no se recomienda desarrollar directamente sobre main en este laboratorio?**

**Respuesta:** No se recomienda porque main representa la rama estable. Trabajar en una rama aparte permite probar, revisar y aprobar los cambios mediante Pull Request antes de integrarlos.

Pregunta 2
**¿Qué problema se evita al utilizar --skip-git al crear el proyecto Angular?**

**Respuesta:** Evita crear un segundo repositorio Git dentro de frontend. Así, todo el proyecto se controla desde el repositorio principal.

Pregunta 3
**¿Qué verifica npm run build en esta etapa del laboratorio?**

**Respuesta:** Verifica que Angular pueda compilar la aplicación y generar correctamente los archivos de producción sin errores.

Pregunta 4
**¿Qué utilidad tiene revisar git status o git diff --cached antes de realizar un commit?**

**Respuesta:** Permite revisar qué archivos y cambios se incluirán en el commit, evitando agregar archivos erróneos, secretos o cambios incompletos.

Pregunta 5
**¿Qué evento activa el workflow ci.yml?**

**Respuesta:** Se activa cuando se crea o actualiza un Pull Request cuya rama destino es main.

Pregunta 6
**En runs-on: ubuntu-latest, ¿qué representa ubuntu-latest?**

**Respuesta:** Representa una máquina virtual Linux administrada por GitHub Actions donde se ejecuta el workflow.

Pregunta 7
**Ordene las etapas de validación que ejecuta el job frontend y explique por qué npm ci se ejecuta antes que las pruebas.**

**Respuesta:** El orden es: obtener código, configurar Node.js, instalar dependencias con npm ci, ejecutar pruebas y construir Angular. npm ci se ejecuta antes porque instala las dependencias exactas necesarias para ejecutar las pruebas y compilar el proyecto.

Pregunta 8
**Después del push, indique qué etapa del pipeline falla y qué ocurre con las etapas siguientes.**

**Respuesta:** Falla la etapa de ejecución de pruebas porque la prueba esperaba un título distinto al real. Las etapas siguientes, como la construcción de Angular, no se ejecutan.

Pregunta 9
**¿Debería integrarse este Pull Request a main mientras el pipeline está fallando? Justifique.**

**Respuesta:** No. Un Pull Request con el pipeline fallando no debe integrarse porque no cumple las validaciones automáticas y podría incorporar errores a main.

Pregunta 10
**Clasifique cada elemento como “versionable”, “variable/configuración” o “secreto/no versionable”: package.json, API_URL pública, AWS_REGION, DB_PASSWORD, API_TOKEN, terraform.tfstate.**

**Respuesta:**

- package.json: versionable.
- API_URL pública: variable/configuración.
- AWS_REGION: variable/configuración.
- DB_PASSWORD: secreto/no versionable.
- API_TOKEN: secreto/no versionable.
- terraform.tfstate: secreto/no versionable.

Pregunta 11
**¿Por qué una contraseña o token no debe escribirse directamente dentro de ci.yml, cd.yml o un archivo TypeScript del frontend?**

**Respuesta:** Porque podría quedar expuesto en el repositorio o en el historial de commits. Los valores sensibles deben almacenarse como GitHub Secrets.

Pregunta 12
**Si un secreto real fue incluido en un commit y luego se agrega su archivo a .gitignore, ¿queda solucionado el problema? Explique qué acción adicional debe realizarse.**

**Respuesta:** No. .gitignore evita futuros commits, pero no elimina el secreto del historial. Se debe revocar o rotar la credencial y eliminarla del historial si es necesario.

Pregunta 13
**¿Qué diferencia existe entre terraform validate, terraform plan y terraform apply?**

**Respuesta:** terraform validate revisa la sintaxis y consistencia de la configuración. terraform plan muestra los cambios que se aplicarían. terraform apply ejecuta realmente esos cambios.

Pregunta 14
**¿Por qué ci.yml se activa con pull_request y cd.yml se activa con push sobre main?**

**Respuesta:** CI se activa en Pull Request para validar los cambios antes de integrarlos. CD se activa con push a main porque despliega solo código que ya fue integrado y aprobado.

Pregunta 15
**¿Qué función cumple Terraform dentro de este flujo de CD?**

**Respuesta:** Terraform prepara de forma repetible el ambiente de staging simulado, copiando el build de Angular hacia la carpeta staging.

Pregunta 16
**¿Por qué el workflow usa ${{ secrets.DEMO_TOKEN }} en lugar de escribir el valor directamente?**

**Respuesta:** Porque GitHub Secrets protege el valor sensible y evita escribirlo directamente en el repositorio o exponerlo en el código.