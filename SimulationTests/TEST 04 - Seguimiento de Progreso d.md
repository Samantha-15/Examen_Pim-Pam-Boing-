#### **TEST 04 - Seguimiento de Progreso de Niveles**



**Nombre:** Estatus de Avance y Tiempo Empleado



**Descripción:** Muestra el estado actual de cada perfil en los diferentes niveles y cuánto tiempo invirtieron.



**Objetivo:** Corroborar que el sistema actualiza correctamente el estado a "Completado" o "Desbloqueado" tras una sesión.



**Criterios de Aprobación:** El campo tiempo\_empleado debe ser coherente con la duración de una partida normal.



**Estatus:** Exitoso



**Código SQL:**



SQL

SELECT perfil\_id, nivel\_id, estatus, tiempo\_empleado 

FROM progreso\_niveles;



**Evidencias:**

