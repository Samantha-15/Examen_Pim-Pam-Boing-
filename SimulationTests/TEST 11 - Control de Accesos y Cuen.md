TEST 11 - Control de Accesos y Cuentas de Usuario

Nombre: Auditoría de Login y Estatus de Cuenta

Descripción: Monitorea el correo electrónico, el estado actual de la
cuenta (Activo, Bloqueado, Suspendido) y la marca de tiempo de su último
acceso.

Objetivo: Identificar cuentas inactivas o bloqueadas y validar que el
sistema de logueo actualice correctamente la columna ultimo_acceso.

Criterios de Aprobación: Todas las cuentas deben tener un correo
electrónico válido y una fecha de acceso que coincida con la actividad
reciente.

Estatus: Exitoso

Código SQL:

SQL SELECT id, email, estatus, ultimo_acceso FROM usuarios;

Evidencias:
![Test 01 - Consulta de Registros](https://github.com/Samantha-15/Examen_Pim-Pam-Boing-/blob/main/SimulationTests/test11.jpeg)
