# Equipo XX — Esquema relacional del proyecto

**Dominio de negocio:**

**Integrantes:**
-
-
-

**Enlace al diagrama E/R del jueves 17** (dbdiagram.io, Mermaid o archivo en el repositorio del proyecto):

---

## 1. Esquema relacional
PLAN(**id_plan**, nombre_plan UNIQUE, costo_mensual)

SOCIO(**num_socio**, nombre, fecha_nacimiento, correo, id_plan → PLAN)

TELEFONO_SOCIO(**num_socio** → SOCIO, **telefono**)

LOCKER(**num_locker**, ubicacion, num_socio? UNIQUE → SOCIO)

INSTRUCTOR(**num_empleado**, nombre, especialidad, num_supervisor? → INSTRUCTOR)

CLASE(**id_clase**, nombre, cupo_maximo, num_empleado → INSTRUCTOR)

SESION(**id_clase** → CLASE, **num_sesion**, fecha, hora_inicio, salon)

INSCRIPCION(**num_socio** → SOCIO, **id_clase** → CLASE, **fecha_inscripcion**, estatus)
<!-- Transformen su E/R completo con la notación de guias/notacion.md.
     Todas las tablas, todas las PK, todas las FK y el ? donde corresponda. -->

```

```

## 2. Relaciones N:M y cómo las resolvieron

<!-- Una fila por cada relación N:M de su E/R. -->

| Relación en el E/R | Tabla intermedia | Llave primaria de la tabla intermedia | ¿Se puede repetir la misma pareja? ¿Por qué? |
|---|---|---|---|
| | | | |

## 3. Relaciones 1:1, recursivas, débiles y multivaluados

<!-- Si su E/R no tiene alguno de estos casos, escriban "No aplica". -->

| Caso | Dónde aparece en su E/R | Cómo lo resolvieron |
|---|---|---|
| Relación 1:1 | | |
| Relación recursiva | | |
| Entidad débil | | |
| Atributo multivaluado | | |

## 4. Llaves foráneas que admiten NULL

<!-- Toda FK con ? necesita una razón de negocio. -->

| Tabla.columna | Por qué puede quedar vacía |
|---|---|
| | |

## 5. Cambios respecto del E/R del jueves

<!-- Al pasar a tablas casi siempre aparece algo que el E/R no dejaba ver.
     Si cambiaron algo del diagrama, díganlo aquí. Si no cambiaron nada, escriban "Ninguno". -->

-
