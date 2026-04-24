#### **TEST 01 - Validación de Registro de Usuarios y Datos Personales**



**Nombre:** Reporte de Usuarios y Nombres Reales



**Descripción:** Consulta que vincula las credenciales de acceso (email) con la identidad física de los usuarios.



**Objetivo:** Verificar la integridad de la relación entre la tabla usuarios y persona\_fisica, asegurando que cada cuenta de correo esté asociada a un nombre y apellido.



**Criterios de Aprobación:** La consulta debe devolver registros donde el correo electrónico coincida con la identidad del usuario sin valores nulos.



**Estatus:** Exitoso



**Código SQL:**

SQL

SELECT u.email, p.nombre, p.primer\_apellido 

FROM usuarios u 

JOIN persona\_fisica p ON u.personas\_id = p.personas\_id;



**Evidencias:**

