TEST 08 - Ejecución de Simulación de Datos (Stress Test)

Nombre: Ejecución de Procedimiento Almacenado de Simulación

Descripción: Prueba de estrés mediante el llamado al procedimiento
sp_simulacion_pinpon_v2.

Objetivo: Generar datos masivos de prueba para medir el rendimiento de
la base de datos bajo carga.

Criterios de Aprobación: El procedimiento debe finalizar sin errores de
timeout y poblar las tablas relacionadas con el número de registros
solicitado.

Estatus: Exitoso

Código SQL:

SQL \-- Prueba rápida: CALL sp_simulacion_pinpon_v2(20, 5, 3); \--
Prueba mediana: CALL sp_simulacion_pinpon_v2(100, 8, 5);

Evidencias:
