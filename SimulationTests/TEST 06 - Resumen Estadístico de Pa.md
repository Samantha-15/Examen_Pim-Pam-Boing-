TEST 06 - Resumen Estadístico de Pagos

Nombre: Conteo de Transacciones por Estatus

Descripción: Agrupa el total de transacciones financieras según su
estado (Aprobado, Rechazado, Pendiente).

Objetivo: Obtener una visión general del flujo de caja y posibles fallos
en la pasarela de pagos.

Criterios de Aprobación: La suma de los totales debe coincidir con el
registro histórico de la tabla.

Estatus: Exitoso

Código SQL:

SQL SELECT estatus, COUNT(\*) as total FROM transacciones_financieras
GROUP BY estatus;

Evidencias:
