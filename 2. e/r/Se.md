# Sistemas de Bases de Datos  
# Proyecto DBS 2025 PAO 1: Entregable 1  
# Segunda Instrucción

## BUSINESS RULES

# 1) Usuarios y Árbol Genealógico
- En FamilySearch.org cada usuario debe tener exactamente un Árbol Genealógico Personal.
- Cada Árbol Genealógico Personal pertenece a un único Usuario.
- Existe un único Árbol Genealógico Compartido en el sistema.
- Un Usuario puede colaborar en el Árbol Genealógico Compartido, pero no en los árboles personales de otros usuarios.

# 2) Personas
- Cada Persona debe tener un Identificador Único.
- Cada persona debe pertenecer a exactamente un Árbol Genealógico (personal o compartido).
- Las personas vivas solo pueden estar en el Árbol Personal del Usuario que las creó.
- Las Personas fallecidas solo pueden estar en el Árbol Compartido.

# 3) Relaciones Familiares
- Cada Relación Familiar vincula exactamente dos Personas.
- Una persona puede tener múltiples Relaciones Familiares.
- Cada Relación Familiar debe especificar el tipo de parentesco (padre, hijo, cónyuge).

# 4) Recuerdos (Multimedia)
- Un Recuerdo es subido por un Usuario.
- Un Recuerdo debe estar asociado a una o más Personas.
- Un Usuario puede subir múltiples Recuerdos.

# 5) Registros Históricos y Fuentes
- Un Registro Histórico puede estar vinculado a múltiples Personas como evidencia.
- Una Fuente conecta una Persona con un Registro Histórico.
- Una Persona puede tener cero o más Fuentes.

# 6) Contribuciones y Cambios
- Cada Contribución es realizada por un Usuario.
- Cada Contribución afecta a una Persona específica.
- Cada Contribución debe registrar la fecha, tipo de cambio y persona modificada.
- Un Usuario puede tener múltiples Contribuciones.

# 7) Privacidad y Control de Acceso
- El Árbol Personal de un Usuario no puede ser visto ni editado por otros Usuarios.
- El Árbol Compartido es visible y editable por todos los Usuarios.
- La información de Personas vivas es privada y solo accesible por su creador.
- La información de Personas Fallecidas es pública y colaborativa.

## Entidades Principales

- Usuario (entidad general)
- UsuarioRegistrado (subclase de Usuario)
- Administrador (subclase de Usuario)
- ÁrbolGenealógico
- Persona
- RelaciónFamiliar
- Recuerdo
- RegistroHistórico
- Fuente
- Contribución

## Relaciones entre Entidades

- UsuarioRegistrado(1,1) — **POSEE** — (1,1)ÁrbolGenealógico: Cada usuario registrado tiene su árbol personal.
- UsuarioRegistrado(1,1) — **SUBE** — (0,N)Recuerdo: Un usuario registrado puede subir muchos recuerdos.
- UsuarioRegistrado(1,1) — **REALIZA** — (0,N)Contribución: Puede hacer múltiples contribuciones.
- Administrador(1,1) — **MODERA** — (0,N)Recuerdo: Supervisa recuerdos subidos por los usuarios.
- Administrador(1,1) — **GESTIONA** — (0,N)RegistroHistórico: Puede cargar o editar registros históricos y asignarlos a colecciones.
- Administrador(1,1) — **CREA_USUARIO** — (0,N)UsuarioRegistrado: Tiene permisos para crear nuevas cuentas.
- ÁrbolGenealógico(1,1) — **INCLUYE** — (1,N)Persona: Un árbol incluye muchas personas. Cada persona pertenece a un solo árbol.
- RelaciónFamiliar(1,1) — **INVOLUCRA_ORIGEN** — (1,N)Persona: Persona que declara el vínculo.
- RelaciónFamiliar(1,1) — **INVOLUCRA_DESTINO** — (1,N)Persona: Persona a quien se refiere el vínculo.
- Recuerdo(1,N) — **ASOCIA** — (1,N)Persona: Un recuerdo debe estar asociado al menos a una persona.
- Fuente(1,1) — **CITA** — (1,1)RegistroHistórico: Una fuente debe referenciar exactamente un registro.
- Persona(0,N) — **TIENE** — (1,1)Fuente: Una persona puede tener cero o más fuentes.
- Contribución(1,1) — **MODIFICA** — (1,1)Persona: Cada contribución modifica exactamente una persona.

**Nota:** 'RelaciónFamiliar' incluye el atributo 'tipoParentesco' con valores como: padre, hijo, cónyuge, etc.

## Atributos de Entidades

| ENTIDAD               | CLAVE PRIMARIA  | ATRIBUTOS                          | DESCRIPCIÓN |
|-----------------------|-----------------|------------------------------------|-------------|
| **Usuario**           | idUsuario       | email, nombre                      | Representa a un individuo registrado en la plataforma. |
| **UsuarioRegistrado** | idUsuario       | email, nombre                      | Usuario que puede crear árboles, subir recuerdos y realizar contribuciones. Subclase de Usuario. |
| **Administrador**     | idUsuario       | email, nombre                      | Usuario con funciones administrativas como crear cuentas, moderar, y gestionar registros. Sub. Usuario
| **ÁrbolGenealógico**  | idArbol         | tipoArbol                          | Representa un conjunto organizado de personas. Puede ser personal o compartido. |
| **Persona**           | idPersona       | nombres, apellidos, fechaNacimiento, estado | Individuo en un árbol. Puede estar vivo o fallecido. |
| **RelaciónFamiliar**  | idRelacion      | tipoParentesco                     | Relación entre dos personas. Ej.: padre, hijo, cónyuge. |
| **Recuerdo**          | idRecuerdo      | tipoRecuerdo                       | Archivo multimedia (imagen, historia, audio...). |
| **RegistroHistórico** | idRegistro      | tipoDocumento                      | Documento oficial escaneado usado como evidencia. |
| **Fuente**            | idFuente        | comentario *(opcional)*            | Vínculo entre Persona y RegistroHistórico. Puede incluir observaciones. |
| **Contribución**      | idContribucion  | tipoCambio, fecha                  | Acción registrada que modifica a una persona. Se guarda para trazabilidad. |