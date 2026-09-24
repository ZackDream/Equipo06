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

## 2. Relaciones N:M y cómo las resolvieron

| Relación en el E/R | Tabla intermedia | Llave primaria de la tabla intermedia | ¿Se puede repetir la misma pareja? ¿Por qué? |
|---|---|---|---|
| SOCIO – CLASE (un socio se inscribe a varias clases y una clase tiene muchos socios) | INSCRIPCION | (`num_socio`, `id_clase`, `fecha_inscripcion`) | Sí, en fechas distintas. Un socio puede darse de baja de Yoga en marzo y reinscribirse en junio: es la misma pareja socio-clase, pero son dos inscripciones distintas. Por eso `fecha_inscripcion` forma parte de la llave. Lo que no puede repetirse es la misma pareja con la misma fecha. |

## 3. Relaciones 1:1, recursivas, débiles y multivaluados

| Caso | Dónde aparece en su E/R | Cómo lo resolvieron |
|---|---|---|
| Relación 1:1 | SOCIO – LOCKER (un socio renta a lo más un locker y un locker lo renta a lo más un socio) | Se puso la FK en LOCKER: `num_socio? UNIQUE → SOCIO`. Admite NULL porque hay lockers libres, y es `UNIQUE` para que un mismo socio no tenga dos lockers. |
| Relación recursiva | INSTRUCTOR supervisa a INSTRUCTOR | Columna `num_supervisor? → INSTRUCTOR` dentro de la misma tabla, que apunta a `num_empleado`. Admite NULL porque la coordinadora general no tiene supervisor. |
| Entidad débil | SESION depende de CLASE (la "sesión 3" no significa nada sin su clase) | PK compuesta (`id_clase` → CLASE, `num_sesion`): hereda la llave de CLASE y agrega el número de sesión como discriminador. |
| Atributo multivaluado | Teléfonos de un socio (puede dejar uno o varios) | Tabla aparte TELEFONO_SOCIO con PK compuesta (`num_socio` → SOCIO, `telefono`): una fila por cada teléfono. |

## 4. Llaves foráneas que admiten NULL

| Tabla.columna | Por qué puede quedar vacía |
|---|---|
| LOCKER.num_socio | Hay lockers libres: un locker que nadie ha rentado no apunta a ningún socio. |
| INSTRUCTOR.num_supervisor | La coordinadora general no tiene supervisor. |

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
