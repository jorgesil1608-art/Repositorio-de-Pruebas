# Calidad y verificación: Comprobaciones obligatorias y
criterios de revision para caracteristicas de Cucumber

Es obligatorio que cada característica de Cucumber generada
cumpla con los siguientes criterios de calidad y verificación
para asegurar su efectividad y mantenibilidad:

### Criterios de Aseguramiento de Calidad

**COMPROBACIONES OBLIGATORIAS:**
- [ ] Todos los escenarios son ** ejecutables ** y
**comprobables**
- [ ] Cada caracteristica tiene al Jenos 1 escenario `@smoke` (ruta crítica)
- [ ] Las pruebas de valores limite están incluidas para entradas numericas
- [ ] Los pasos usan **lenguaje declarativo** (evitar detalles de implementación)
- [ ] Los datos de prueba son **independientes** entre escenarios
- [ ] Las caracteristicas son **cohesivas** y **bien organizadas**
- [ ] La estrategia de etiquetado es **consistente** en todas las características
- [ ] La documentación es **completa** y **accionable**
- [ ] Si se generan características a partir de **Historias de Usuario** con ID de Jira, cada escenario tiene la etiqueta correspondiente `@ID-1234`
 
 ---
