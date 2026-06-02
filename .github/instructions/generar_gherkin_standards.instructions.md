## Objetivo
Definir estandares y mejores prácticas para  generar escenarios BDD con Cucumber.
---
## Estándares Obligatorios de Cucumber

**REQUISITOS OBLIGATORIOS:**
- Todos los escensarios DEBEN ser **ejecutables** y **comprobables**
- Usar **Lenguaje delcarativo** (QUE, NO COMO)
- Seguir estrictamente la estructura **Fiven-When-Then** (Dado-Cuando-Entonces)
Asegurar **reutilizacion de pasos** entre caracteristicas
- Aplicar **principios SOLID** al diseñar escenarios
- Incluir **pruebas basadas en datos** donde sea apropiado
- implementar escenarios de **manejo adecuado de errores** **PROHIBIDO:** Pasos que comienzan con "O", "Pero","E","*", o cualquier otra palabra **CORRECTO**: Usar "y" para concatenar multiples aserciones o condiciones altervativas.

**Requisitos Técnicos de Validacionn:**
- Cada escennarios DEBE tener **Criterios de aceptacion** Claros
- Incluir escenarios de **prueba de valores limites**
- Asgurar ** independencia de datos de prueba** entre escenarios

---
## Estrategias Avanzadas de Etiqueta BDD 02:15:20
**Etiqueta Primarias:**
- `@smoke: Funcionalidad escencial que debe funcionar (tipicamente 1-2 escenarios por caracteristica)
- `@regression`: Escenarios importantes incluyendo validaciones, manejo de errores, casos límite
**Etiqueta Secundarias:**
- Tipo de entorno: `@web`, `@mobile`, `@api`
- Areas funcionales (ejemplos): `@autentication`,`@users`, `@products`,`@orders`,`@payments`, `@administration`, `@reports`, etc
- Si la documentacion son historias de usuario con ID de Jira Añadir etiqueta con el ID: `@ID-1234`

**Ejemplos de etiquetado:**
```gherkin
@smoke @autentication
Escenario: Login exitoso al sistema

@regression @autentication
Escenario: Login Fallido por credenciales incorrectas

@smoke @expedientes
Escenario: Consultar expediente existente

@regression @facturas
Escenario: Validar campo obligatorio en factura
```


---
## Estructura de Archivos Requerida
```
${output_directory}/
├── README.md         #Comprehensive documentation (ROOT LEVEL)
├── features/         #BDDfeature files directory
│   ├── autentication.feature
│   ├── expediente-management.feature
│   ├── turboo-alta-facturas.feature
│   └── ...
```

**Importante:**
- **Los archivos .feature** van SOLO en el subdirectorio `features/`
- **README.md** se debe ubicar en la raiz de `${output_directory}/` (NO en el directorio `features/`)

---
### Estructura de Escenarios y Mejores Prácticas
**Estructura de Escenarios:**
```gherkin
#lenguage: es
Característica: [Descriptive funtionality name]
  Como [user type]
  Quiero [perform an action]
  Para [obtain a benefit]

  @smoke @[functional_area]
    Escenario: [Success scenario description]
    Dado que [initial condition]
    Y [additional condition if necessary]
    Cuando [user action]
    Entonces [expected result]
    Y [additional validation if necessary]

  @regression @[functional area] @validaciones
    Escenario: [Validation scenario description]
    Dado que [initial condition]
    Cuando [action that causes error]
    Entonces [expected error result]
    Y [specific error validation]
```

**Principios de Escritura:**


1. **Lenguaje Natural**: Usar terminologia del dominio de negocio
2. **Declarativo vs Imperativo**: Describir QUE no COMO
3. **Independencia**: Cada escenario debe ser independiente
4. **Reutilizacion**: Usar pasos que puedan ser reutilizados
5. **Granularidad**: Un escenario por comportamiento especifico

...

### Convenciones de Nomenclatura

**Archivos de Características:**
Usar kebab-case para nombres de archivos
. Nombres descriptivos del area funcional
- Ejemplos: `user-authentication. feature`, `invoice-management.feature`

**Nombres de Escenarios:**
- Descriptivos y concisos
- Ejemplos: "Crear nueva factura con datos validos", "Validar
campos obligatorios"

** Etiquetas :**
- Usar minúsculas
- Separar palabras con guiones bajos si es necesario
- Ejemplos: @smoke, @regression', `@user_management'

I

### Patrones de Datos de Prueba

**Esquemas de Escenario para Datos Múltiples:**
```gherkin

@regression @validaciones
Esquema del escenario: Validate [field] format
  Dado que estoy en la página "[page]"
  Cuando ingreso "<value>" en el campo "[field]"
  Entonces debería ver el mensaje "<error_message>"

  Ejemplos:
    | value           | error message                       |   
    | invalid email   | Incorrect email format              |
    | empty_text      | This field is mandatory             |
    |long_text        | Maximum 50 characters allowed       |
    ```







