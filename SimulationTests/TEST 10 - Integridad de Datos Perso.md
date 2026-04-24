TEST 10 - Integridad de Datos Personales (Personas Físicas)

Nombre: Listado de Identidad de Usuarios

Descripción: Muestra los nombres completos, apellidos y género de las
personas registradas en el sistema.

Objetivo: Asegurar que los datos demográficos básicos se capturen sin
errores y que el campo genero cumpla con los valores permitidos (M/F).

Criterios de Aprobación: Los nombres y apellidos deben estar debidamente
capitalizados y no presentar caracteres extraños.

Estatus: Exitoso

Código SQL:

SQL SELECT nombre, primer_apellido, segundo_apellido, genero FROM
persona_física;

Evidencias:
