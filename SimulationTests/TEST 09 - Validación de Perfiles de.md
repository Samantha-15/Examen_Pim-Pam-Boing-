TEST 09 - Validación de Perfiles de Jugadores

Nombre: Reporte de Avatares y Estatus de Perfil

Descripción: Consulta los datos públicos de los jugadores, incluyendo su
apodo, la ruta de su avatar y la fecha en que se registraron.

Objetivo: Verificar que la personalización del perfil (nickname y
avatar) se esté almacenando correctamente y que el estatus por defecto
sea coherente.

Criterios de Aprobación: Los campos apodo y avatar_url no deben estar
vacíos y el formato de imagen (.png) debe ser correcto.

Estatus: Exitoso

Código SQL:

SQL SELECT apodo, avatar_url, fecha_registro, estatus FROM
perfiles_jugadores;

Evidencias:
![Test 01 - Consulta de Registros](https://github.com/Samantha-15/Examen_Pim-Pam-Boing-/blob/main/SimulationTests/test9.jpeg)
