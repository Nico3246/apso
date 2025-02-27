# apso
# Apuntes para Prácticas A.P.S.O. - Manejo de la Shell (I)

Este documento reúne los apuntes y pasos clave de las prácticas **1.1** y **1.2** para que puedas repasar y prepararte para el examen.

## Contenido

- [Conceptos y Comandos Básicos](#conceptos-y-comandos-básicos)
- [Práctica 1.1 - Manejo de la Shell (I)](#práctica-11---manejo-de-la-shell-i)
- [Práctica 1.2 - Manejo de la Shell (I)](#práctica-12---manejo-de-la-shell-i)
- [Recomendaciones para el Examen](#recomendaciones-para-el-examen)

---

## Conceptos y Comandos Básicos

### Rutas Absolutas vs. Relativas
- **Absolutas:** Inician desde la raíz (ej. `/home/velez/...` o `/home/user-apso/...`).
- **Relativas:** Se indican en relación al directorio actual (ej. `prac1` o `./ModuloI/Practica1/`).

### Comandos Fundamentales
- **Navegación:**
  - `cd`: Cambiar de directorio.
  - `pwd`: Mostrar el directorio actual.
- **Directorios:**
  - `mkdir`: Crear directorios.
    - Con `-p` se crean estructuras anidadas.
  - `rmdir`: Eliminar directorios vacíos.
  - `rm -r`: Eliminar directorios y su contenido de manera recursiva.
- **Ficheros:**
  - `cp`: Copiar ficheros.
  - `mv`: Mover o renombrar ficheros.
  - `rm`: Eliminar ficheros.
- **Visualización y Edición:**
  - `ls -l`: Listar en formato largo.
  - `cat` y `more`: Mostrar el contenido de ficheros (con `more` se puede pausar la salida).
  - `joe`: Editor de texto.
- **Wildcards (Construcciones Globales):**
  - `*` para cualquier cadena.
  - `?` para un solo carácter.
  - `[]` para definir conjuntos o rangos de caracteres.

---

## Práctica 1.1 - Manejo de la Shell (I)

### Estructura y Pasos Clave

1. **Crear Directorio de Trabajo:**  
   - Crear `prac1` en el directorio personal (usando rutas relativas):
     ```bash
     mkdir prac1
     ```

2. **Copiar Fichero (p1.txt):**  
   - Copiar desde `/home/so/velez/MI/p1.txt` a `~/prac1` (usando rutas absolutas):
     ```bash
     cp /home/so/velez/MI/p1.txt /home/velez/prac1
     ```

3. **Nueva Sesión y Edición:**  
   - Abrir una nueva sesión, cambiar a `prac1` y editar `p1.txt` con `joe` (usando ruta absoluta):
     ```bash
     cd prac1
     joe /home/velez/prac1/p1.txt
     ```

4. **Crear y Navegar Directorios:**  
   - Crear `prac11` usando ruta absoluta y moverse a él (ruta relativa):
     ```bash
     mkdir /home/velez/prac1/prac11
     cd prac11
     ```

5. **Crear Múltiples Directorios en un Solo Comando:**  
   - Crear `prac12`, `prac13`, `prac14` y `prac15` como hijos de `prac1`:
     ```bash
     mkdir ../prac12 ../prac13 ../prac14 ../prac15
     ```

6. **Navegación y Visualización de Ficheros:**  
   - Ir al directorio raíz y visualizar `p1.txt`:
     ```bash
     cd /
     more home/velez/prac1/p1.txt
     cd home/velez/prac1/prac13
     more ../p1.txt
     ```

7. **Crear Ficheros de Prueba con `joe`:**  
   - En `prac13`, crear `prueba13` (ruta absoluta) con el mensaje:
     > "Esto es un fichero de prueba perteneciente al usuario (tu nombre de usuario)"
     ```bash
     joe /home/velez/prac1/prac13/prueba13
     ```
   - En `prac12`, crear `prueba12` (ruta relativa):
     ```bash
     joe ../prac12/prueba12
     ```

8. **Crear Fichero Ejemplo en `prac11`:**  
   - Crear `ejemplo01` con el mensaje:
     > "Esto es un fichero ejemplo creado con el joe en la practica 1"
     ```bash
     joe ../prac11/ejemplo01
     ```

9. **Copiar Ficheros entre Directorios:**  
   - Copiar `prueba12` y `prueba13` a `prac11` (rutas relativas):
     ```bash
     cp prueba13 ../prac12/prueba12 ../prac11
     ```

10. **Copiar y Renombrar Fichero:**  
    - Copiar `prueba12` de `prac12` a `prac14`, renombrándolo a `prueba14`:
      ```bash
      cp ../prac12/prueba12 ../prac14/prueba14
      ```

11. **Crear Subdirectorios en `prac12`:**  
    - Crear `temp1` y `temp2`:
      ```bash
      mkdir ../prac12/temp1 ../prac12/temp2
      ```

12. **Mover y Copiar Ficheros con un Solo Comando:**  
    - Mover `prueba13` a `temp1`:
      ```bash
      mv prac13/prueba13 prac12/temp1
      ```
    - Copiar `prueba12` y `prueba14` a `temp1`:
      ```bash
      cp prac12/prueba12 prac14/prueba14 prac12/temp1
      ```

13. **Uso de Wildcards:**  
    - Copiar ficheros en `temp1` que:
      - Empiecen por "p"
      - Tengan penúltimo carácter 1
      - Terminen en un dígito entre 1 y 5  
      Hacia `temp2`:
      ```bash
      cp prac12/temp1/p*1[1-5] prac12/temp2
      ```

14. **Eliminar Ficheros con Wildcards:**  
    - Borrar ficheros de `temp1` cuyo penúltimo carácter sea un número (ruta absoluta):
      ```bash
      rm /home/velez/prac1/prac12/temp1/*[0-9]?
      ```

15. **Borrar Directorios:**  
    - Eliminar `temp1` (ruta absoluta):
      ```bash
      rmdir /home/velez/prac1/prac12/temp1
      ```
    - Eliminar `temp2` y su contenido (ruta relativa):
      ```bash
      rm -r prac12/temp2
      ```

16. **Regresar al Directorio Personal:**  
    - Volver a casa y verificar:
      ```bash
      cd
      pwd
      ```

17. **Guardar Cambios en el Fichero:**  
    - En la sesión de `joe`, guardar `p1.txt` como `solp1.txt` en `prac1` usando la secuencia de guardado de `joe`.

18. **Cambiar Permisos del Fichero:**  
    - Aplicar permisos 700 a `solp1.txt`:
      ```bash
      chmod 700 prac1/solp1.txt
      ```

---

## Práctica 1.2 - Manejo de la Shell (I)

### Estructura y Pasos Clave

1. **Inicio y Verificación:**
   - Mostrar mensaje de inicio:
     ```bash
     echo "Practica 1: Manejo de Shell - Inicio ..."
     ```
   - Visualizar el directorio actual:
     ```bash
     pwd
     ```

2. **Listados Detallados:**
   - Mostrar contenido del directorio actual:
     ```bash
     ls -l
     ```

3. **Crear Directorios:**
   - Crear el directorio `ModuloI` en el directorio de usuario:
     ```bash
     mkdir ModuloI
     mkdir ./ModuloI
     ```

4. **Crear Directorio Usando Ruta Absoluta:**
   - Dentro de `ModuloI`, crear `Practica1`:
     ```bash
     mkdir /home/user-apso/ModuloI/Practica1
     ```

5. **Cambio de Directorio:**
   - Acceder a `Practica1` usando ruta relativa:
     ```bash
     cd ./ModuloI/Practica1/
     ```

6. **Crear Estructura de Directorios Anidados:**
   - Crear la estructura `Datos/Temporal` y `Datos/basura`:
     ```bash
     mkdir -p /home/user-apso/ModuloI/Practica1/Datos/Temporal
     mkdir /home/user-apso/ModuloI/Practica1/Datos/basura
     ```

7. **Listados con Rutas Absolutas y Relativas:**
   - Visualizar el contenido del directorio de usuario:
     ```bash
     ls -l /home/user-apso/
     ls -l ~
     ```
   - Visualizar el contenido del directorio raíz (ruta relativa):
     ```bash
     ls -l ../..
     ```

8. **Copiar Ficheros Usando Rutas Relativas:**
   - Copiar los ficheros `soneto` y `cancion` de `/home/so/ficheros` a `Practica1`:
     ```bash
     cp ../../../so/ficheros/soneto ../../../so/ficheros/cancion .
     ```

9. **Mover y Renombrar Ficheros:**
   - Copiar `soneto` a `Datos/Temporal` renombrándolo a `estrofa`:
     ```bash
     cp ./Practica1/soneto ./Practica1/Datos/Temporal/estrofa
     ```
   - Mover `cancion` a `Datos`:
     ```bash
     mv ./Practica1/cancion ./Practica1/Datos/
     ```

10. **Visualización y Edición de Ficheros:**
    - Visualizar el contenido de `estrofa`:
      ```bash
      more ./Practica1/Datos/Temporal/estrofa
      cat ./Practica1/Datos/Temporal/estrofa
      joe ./Practica1/Datos/Temporal/estrofa
      ```

11. **Renombrar Fichero:**
    - Cambiar el nombre de `soneto` a `verso`:
      ```bash
      mv ./Practica1/soneto ./Practica1/verso
      ```

12. **Operaciones con Wildcards y Listados Detallados:**
    - Copiar ficheros de `/home/so/ficheros` que comiencen con "f" a `Datos`:
      ```bash
      cp /home/so/ficheros/f* ./Practica1/Datos/
      ```
    - Listar ficheros en `/home/so/ficheros` con distintos patrones:
      - Que terminen en un número:
        ```bash
        ls -l *[0-9]
        ```
      - Que no comiencen con vocal:
        ```bash
        ls -l [!aAeEiIoOuU]*
        ```
      - Que no comiencen con número:
        ```bash
        ls -l [!0-9]*
        ```
      - Con extensión de exactamente 3 caracteres:
        ```bash
        ls -l *.???
        ```
      - Con extensión de más de 3 caracteres:
        ```bash
        ls -l *.????*
        ```
      - Con extensión `bak` y nombre que comience por una letra:
        ```bash
        ls -l [a-zA-Z]*.bak
        ```

13. **Eliminación de Ficheros y Directorios:**
    - Borrar ficheros en `Datos` cuyo nombre tenga dos caracteres:
      ```bash
      rm ??
      ```
    - Copiar ficheros de `Datos` que terminen en número a `Temporal`:
      ```bash
      cp ./*[0-9] ./Temporal/
      ```
    - Visualizar el contenido de `fichcancion` (paginado):
      ```bash
      more fichcancion
      ```
    - Eliminar el directorio `Temporal`:
      ```bash
      cd ~/ModuloI/Practica1/Datos/
      rm -r ./Temporal
      ```

14. **Gestión de Directorio `tmpfiles`:**
    - Crear el directorio `tmpfiles` dentro de `Datos`:
      ```bash
      mkdir tmpfiles
      ```
    - Dentro de `tmpfiles`, crear:
      - `file1.txt` con `joe`:
        ```bash
        cd ./tmpfiles/
        joe file1.txt
        ```
      - `file2.txt` usando `cat` con redirección:
        ```bash
        cat >file2.txt
        ```
    - Mostrar la concatenación de ambos archivos:
      ```bash
      cat file1.txt file2.txt
      ```
    - Editar `file1.txt` para agregar al menos 20 líneas y visualizarlo con pausas cada 5 líneas:
      ```bash
      joe file1.txt
      more -5 file1.txt
      ```
    - Crear un fichero `file-text.txt` (usando `cat` o `joe`):
      ```bash
      cat >file-text.txt
      joe file-text.txt
      ```

15. **Listados Específicos y Acceso Rápido:**
    - Listar ficheros que contengan un guión:
      ```bash
      ls -l *[-]*
      ```
    - Acceder rápidamente al directorio de usuario:
      ```bash
      cd
      ```
      (equivalente a `cd ~` o `cd /home/user-apso`).

16. **Eliminación con Rutas Absolutas y Relativas:**
    - Eliminar `file2.txt` usando ruta absoluta:
      ```bash
      rm /home/user-apso/ModuloI/Practica1/Datos/tmpfiles/file2.txt
      ```
    - Borrar el directorio `tmpfiles` (primero eliminar su contenido, luego el directorio):
      ```bash
      rm ./tmpfiles/*
      rmdir ./tmpfiles
      ```

17. **Comandos Finales:**
    - Limpiar la pantalla:
      ```bash
      clear
      ```
    - Mostrar mensaje de finalización:
      ```bash
      echo "Práctica 1: Manejo de Shell… Finalizada"
      ```
    - Salir del sistema:
      ```bash
      exit
      ```

---

## Recomendaciones para el Examen

- **Verificar Rutas y Comandos:**  
  Asegúrate de utilizar correctamente rutas relativas y absolutas, y revisa la salida de cada comando para confirmar que se ejecutó correctamente.

- **Uso del Tabulador y `man`:**  
  Emplea la tecla *Tab* para autocompletar rutas y el comando `man` para consultar la ayuda de cualquier comando.

- **Comprender Wildcards:**  
  Practica el uso de `*`, `?` y `[]` para trabajar de forma eficiente con conjuntos de ficheros.

- **Precisión en Nombres y Directorios:**  
  Presta atención a mayúsculas y minúsculas, así como a la estructura de directorios para evitar errores.

- **Revisión de Ficheros y Permisos:**  
  Verifica el contenido de los ficheros con `cat` o `more`, y revisa los permisos con `chmod` cuando sea necesario.

---

*Guarda este archivo como `README.md` en tu repositorio o en tu sistema para consultarlo antes del examen. ¡Buena suerte!*
