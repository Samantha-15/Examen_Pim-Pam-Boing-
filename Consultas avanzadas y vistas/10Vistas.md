# Vistas de SQL para KPIs

Este documento contiene las 10 vistas desarrolladas para el análisis de datos del proyecto.

## 1. kpi_1_conversion_premium
CREATE 
    ALGORITHM = UNDEFINED 
    DEFINER = `root`@`localhost` 
    SQL SECURITY DEFINER
VIEW `kpi_1_conversion_premium` AS
    SELECT 
        (((SELECT 
                COUNT(0)
            FROM
                `licencias`
            WHERE
                (`licencias`.`estatus` = 'Vigente')) / (SELECT 
                COUNT(0)
            FROM
                `personas`)) * 100) AS `tasa_conversion_porcentaje`

## 2. kpi_2_arpu
CREATE 
    ALGORITHM = UNDEFINED 
    DEFINER = `root`@`localhost` 
    SQL SECURITY DEFINER
VIEW `kpi_2_arpu` AS
    SELECT 
        (SUM(`transacciones_financieras`.`monto`) / COUNT(0)) AS `ingreso_promedio_por_plan`
    FROM
        `transacciones_financieras`
    WHERE
        (`transacciones_financieras`.`estatus` = 'Aprobado')

## 3. kpi_3_abandono_checkout
CREATE 
    ALGORITHM = UNDEFINED 
    DEFINER = `root`@`localhost` 
    SQL SECURITY DEFINER
VIEW `kpi_3_abandono_checkout` AS
    SELECT 
        ((COUNT((CASE
            WHEN (`transacciones_financieras`.`estatus` IN ('Cancelado' , 'Rechazado')) THEN 1
        END)) / COUNT(0)) * 100) AS `tasa_abandono_pago`
    FROM
        `transacciones_financieras`
## 4. kpi_4_revenue_mix
CREATE 
    ALGORITHM = UNDEFINED 
    DEFINER = `root`@`localhost` 
    SQL SECURITY DEFINER
VIEW `kpi_4_revenue_mix` AS
    SELECT 
        `p`.`nombre_plan` AS `nombre_plan`,
        SUM(`t`.`monto`) AS `total_ingresos`
    FROM
        ((`transacciones_financieras` `t`
        JOIN `licencias` `l` ON ((`t`.`id` = `l`.`id`)))
        JOIN `planes_licencia` `p` ON ((`l`.`id` = `p`.`id`)))
    WHERE
        (`t`.`estatus` = 'Aprobado')
    GROUP BY `p`.`nombre_plan`

## 5. kpi_5_dispositivos
CREATE 
    ALGORITHM = UNDEFINED 
    DEFINER = `root`@`localhost` 
    SQL SECURITY DEFINER
VIEW `kpi_5_dispositivos` AS
    SELECT 
        `sesiones_juego`.`tipo_dispositivo` AS `tipo_dispositivo`,
        COUNT(0) AS `total_sesiones`
    FROM
        `sesiones_juego`
    GROUP BY `sesiones_juego`.`tipo_dispositivo`

## 6. kpi_6_abandono_niveles
CREATE 
    ALGORITHM = UNDEFINED 
    DEFINER = `root`@`localhost` 
    SQL SECURITY DEFINER
VIEW `kpi_6_abandono_niveles` AS
    SELECT 
        `n`.`nombre_nivel` AS `nombre_nivel`,
        ((COUNT((CASE
            WHEN (`s`.`estatus` = 'Abandonado') THEN 1
        END)) / COUNT(`s`.`id`)) * 100) AS `porcentaje_abandono`
    FROM
        (`niveles` `n`
        LEFT JOIN `sesiones_juego` `s` ON ((`n`.`id` = `s`.`nivel_id`)))
    GROUP BY `n`.`nombre_nivel`

## 7. kpi_7_mrr
CREATE 
    ALGORITHM = UNDEFINED 
    DEFINER = `root`@`localhost` 
    SQL SECURITY DEFINER
VIEW `kpi_7_mrr` AS
    SELECT 
        SUM(`p`.`precio`) AS `ingreso_mensual_recurrente`
    FROM
        (`licencias` `l`
        JOIN `planes_licencia` `p` ON ((`l`.`id` = `p`.`id`)))
    WHERE
        (`l`.`estatus` = 'Vigente')

## 8. kpi_8_crecimiento_usuarios
CREATE 
    ALGORITHM = UNDEFINED 
    DEFINER = `root`@`localhost` 
    SQL SECURITY DEFINER
VIEW `kpi_8_crecimiento_usuarios` AS
    SELECT 
        MONTH(`personas`.`fecha_registro`) AS `mes`,
        YEAR(`personas`.`fecha_registro`) AS `anio`,
        COUNT(0) AS `nuevos_usuarios`
    FROM
        `personas`
    GROUP BY `anio` , `mes`

## 9. kpi_9_rechazo_pagos
CREATE 
    ALGORITHM = UNDEFINED 
    DEFINER = `root`@`localhost` 
    SQL SECURITY DEFINER
VIEW `kpi_9_rechazo_pagos` AS
    SELECT 
        ((COUNT((CASE
            WHEN (`transacciones_financieras`.`estatus` = 'Rechazado') THEN 1
        END)) / COUNT(0)) * 100) AS `tasa_rechazo`
    FROM
        `transacciones_financieras`

## 10. kpi_10_retencion_usuarios
CREATE 
    ALGORITHM = UNDEFINED 
    DEFINER = `root`@`localhost` 
    SQL SECURITY DEFINER
VIEW `kpi_10_retencion_usuarios` AS
    SELECT 
        COUNT(DISTINCT `sesiones_juego`.`perfil_id`) AS `usuarios_activos_30_dias`
    FROM
        `sesiones_juego`
    WHERE
        (`sesiones_juego`.`fecha_inicio` >= (CURDATE() - INTERVAL 30 DAY))