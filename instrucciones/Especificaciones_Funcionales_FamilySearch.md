# Especificaciones Funcionales: FamilySearch.org

## 1. Introducción

En este proyecto, se diseñará e implementará un sistema de base de datos relacional para soportar las operaciones de un sistema de genealogía e historia familiar en línea, basado en la plataforma **FamilySearch.org**. Este documento detalla los requerimientos funcionales, los tipos de usuario y las operaciones que el sistema debe permitir.

## 2. Especificación del Proyecto

FamilySearch.org es una plataforma web que permite a los usuarios construir, explorar y buscar en un árbol genealógico masivo y colaborativo. El objetivo principal es ayudar a las personas a descubrir a sus antepasados, conectar con parientes y preservar su historia familiar. El sistema proporciona acceso a una vasta colección de registros históricos digitalizados por diversas entidades de todo el mundo, que sirven como fuentes primarias para la investigación genealógica. En el caso de Ecuador, gran parte de los datos de nuestros antepasados han sido proporcionados por la Diocesis ecuatoriana de la iglesia catolica.
## 3. Tipos de Usuarios del Sistema

Los usuarios del sistema se clasifican en dos roles principales:

*   **Usuario Registrado:** Es cualquier persona que crea una cuenta en la plataforma, ya sea mediante un registro manual o utilizando un proveedor de identidad de terceros (como Google). No existe una distinción formal para ser "voluntario"; cualquier usuario registrado puede optar por participar en actividades de voluntariado (como la indexación de registros) en cualquier momento. El objetivo de un usuario puede ser investigar su propia historia, construir su árbol genealógico o contribuir a la base de datos comunitaria.
*   **Administrador:** Es el responsable del mantenimiento y la gestión de la plataforma, los datos y los usuarios.

Se debe asumir que el conocimiento informático de los usuarios es variado, por lo que la interfaz del sistema debe ser intuitiva y fácil de usar.

## 4. Requerimientos Funcionales

Los datos requeridos para la base de datos genealógica se pueden clasificar en las siguientes categorías principales:

*   **Personas (Individuos):** Almacena información sobre cada individuo en el árbol genealógico, como nombres, apellidos, fechas y lugares de nacimiento, bautismo, matrimonio y defunción. Cada persona tiene un identificador único.
*   **Familias:** Define las relaciones entre individuos (padres, hijos, cónyuges).
*   **Registros Históricos:** Colecciones de documentos digitalizados (certificados de nacimiento, censos, registros militares, etc.).
*   **Fuentes:** Vínculos que conectan la información de un individuo en el árbol genealógico con un registro histórico que la respalda.
*   **Recuerdos:** Archivos multimedia aportados por los usuarios, como fotografías, historias escritas, documentos y grabaciones de audio, que se asocian a un antepasado.
*   **Usuarios:** Información de las cuentas de los usuarios registrados en la plataforma, incluyendo sus preferencias de privacidad.
*   **Contribuciones y Cambios:** Un historial de todas las modificaciones realizadas sobre los perfiles de los individuos, permitiendo trazabilidad y colaboración.

## 5. Tareas de los Usuarios

### 5.1. Funcionalidades de Nivel Administrador

El Administrador debe poder realizar las siguientes tareas:

*   Gestionar cuentas de usuario (crear, editar, eliminar).
*   Generar informes de uso y actividad de la plataforma.
*   Supervisar y moderar el contenido subido por los usuarios (recuerdos, discusiones).
*   Gestionar las colecciones de registros históricos y los proyectos de indexación.
*   Resolver disputas de datos entre usuarios.
*   Identificar a los usuarios con mayor número de contribuciones.

### 5.2. Funcionalidades de Nivel Usuario Registrado

Los Usuarios Registrados realizan tanto la investigación de su historia familiar como las actividades de voluntariado. Deben poder:

*   **Gestión del Árbol Genealógico:**
    *   Crear, ver y editar su árbol genealógico personal y el árbol compartido.
    *   Añadir nuevas personas al árbol, especificando sus datos vitales (nacimiento, defunción, etc.).
    *   Establecer y editar las relaciones familiares (padres, hijos, cónyuges).
*   **Investigación:**
    *   Buscar antepasados en el árbol genealógico global.
    *   Buscar en la colección de registros históricos utilizando diversos filtros (nombre, lugar, fechas, etc.).
    *   Visualizar las imágenes digitales de los registros históricos originales.
*   **Gestión de Fuentes y Recuerdos:**
    *   Anexar registros históricos como fuentes a los perfiles de sus antepasados.
    *   Subir, etiquetar y gestionar "recuerdos" (fotos, historias, documentos).
*   **Colaboración:**
    *   Ver el historial de cambios de un perfil para entender las contribuciones de otros usuarios.
    *   Colaborar con otros usuarios corrigiendo información o añadiendo nuevas fuentes.
    *   Marcar perfiles de interés para recibir notificaciones sobre cambios.
*   **Actividades de Voluntariado (Indexación):**
    *   Participar en proyectos de indexación para transcribir información de registros históricos digitalizados.
    *   Revisar las indexaciones realizadas por otros voluntarios para garantizar la calidad y precisión de los datos.
    *   Seleccionar proyectos de indexación específicos (por región, idioma o período de tiempo).
    *   Consultar sus estadísticas de contribuciones (número de registros indexados y revisados).

## 6. Control de Acceso de Usuarios

El sistema de base de datos debe proporcionar un acceso controlado a los datos y configuraciones de privacidad para los usuarios:

*   Un **Usuario Registrado** no debe poder acceder a la información privada de la cuenta de otros usuarios.
*   **Privacidad del Árbol Familiar:** Cada usuario puede configurar la visibilidad de su árbol genealógico, haciéndolo público o privado para otros usuarios de la plataforma.
*   **Visibilidad del Perfil:** Cada usuario puede decidir si su perfil de usuario es visible y aparece en los resultados de búsqueda de otros usuarios.
*   **Privacidad de Personas Vivas:** La información de personas vivas es estrictamente privada. Un usuario solo puede ver y editar los perfiles de personas vivas que él mismo haya creado en su espacio privado. No se puede buscar ni ver perfiles de personas vivas creados por otros usuarios.
*   **Colaboración en Personas Fallecidas:** La información de personas fallecidas es pública y colaborativa. Cualquier usuario registrado puede ver y proponer cambios a los perfiles de personas fallecidas en el árbol familiar compartido. 