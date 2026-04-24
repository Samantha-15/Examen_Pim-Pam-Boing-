TEST 07 - Detalle de Transacciones Financieras

Nombre: Reporte de Ingresos por Monto y Fecha

Descripción: Muestra el desglose individual de cada pago registrado en
el sistema.

Objetivo: Validar que los montos se guarden con el formato decimal
correcto y que las fechas de registro sean precisas.

Criterios de Aprobación: No deben existir montos negativos y los estatus
deben reflejar la realidad del pago.

Estatus: Exitoso

Código SQL:

SQL SELECT id, monto, tipo, estatus, fecha_registro FROM
transacciones_financieras;

Evidencia:
