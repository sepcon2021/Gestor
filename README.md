# Gestor

### 1. Enlace de la tabla en la base de datos del gestor

https://drive.google.com/file/d/1WYTOWz0wF2mbbUE19C272cBGhLtuJxKv/view?usp=sharing


### 2. Consulta SQL

El único dato que debes de cambiar es el año el cual está en la parte final de la consulta SQL.
```
WHERE dbo.LOT_ORDENSEGUI.OCAANOORD = VARIABLE_AÑO

```

**VARIABLE_AÑO =  '2022'**



```

SELECT

DATA_CODIGO.OCANUMERO AS NUMERO_ORDEN,

(SELECT
TOP 1
dbo.T_M_ENTE.ENTNOMBRES

FROM
dbo.LOT_ORDENSEGUI
INNER JOIN dbo.T_M_ENTE ON dbo.T_M_ENTE.IDENTCOD = dbo.LOT_ORDENSEGUI.IDPPICODIGO

WHERE dbo.LOT_ORDENSEGUI.OCANUMERO = DATA_CODIGO.OCANUMERO ) AS NOMBRE_EMPRESA ,

(SELECT
TOP 1

dbo.LOT_ORDENSEGUI.MGBSYSUSER AS USUARIO

FROM
dbo.LOT_ORDENSEGUI
INNER JOIN dbo.T_M_ENTE ON dbo.T_M_ENTE.IDENTCOD = dbo.LOT_ORDENSEGUI.IDPPICODIGO

WHERE dbo.LOT_ORDENSEGUI.OCANUMERO = DATA_CODIGO.OCANUMERO ) AS USUARIO ,

(SELECT
TOP 1

dbo.LOT_ORDENSEGUI.OSEGDESCRIP AS DESCRIPCION_USUARIO
FROM
dbo.LOT_ORDENSEGUI
INNER JOIN dbo.T_M_ENTE ON dbo.T_M_ENTE.IDENTCOD = dbo.LOT_ORDENSEGUI.IDPPICODIGO

WHERE dbo.LOT_ORDENSEGUI.OCANUMERO = DATA_CODIGO.OCANUMERO ) AS COMENTARIO_USUARIO ,

(
        SELECT TOP 1 dbo.LOT_ORDENSEGUI.OSEGPUNTAJE
        FROM dbo.LOT_ORDENSEGUI 
        WHERE dbo.LOT_ORDENSEGUI.OCANUMERO = DATA_CODIGO.OCANUMERO AND dbo.LOT_ORDENSEGUI.OSEGCODIGO = '0001'
) AS criterio_1,

(
        SELECT TOP 1 dbo.LOT_ORDENSEGUI.OSEGPUNTAJE
        FROM dbo.LOT_ORDENSEGUI 
        WHERE dbo.LOT_ORDENSEGUI.OCANUMERO = DATA_CODIGO.OCANUMERO AND dbo.LOT_ORDENSEGUI.OSEGCODIGO = '0002'
) AS criterio_2 ,

(
        SELECT TOP 1 dbo.LOT_ORDENSEGUI.OSEGPUNTAJE
        FROM dbo.LOT_ORDENSEGUI 
        WHERE dbo.LOT_ORDENSEGUI.OCANUMERO = DATA_CODIGO.OCANUMERO AND dbo.LOT_ORDENSEGUI.OSEGCODIGO = '0003'
) AS criterio_3 ,

(
        SELECT TOP 1 dbo.LOT_ORDENSEGUI.OSEGPUNTAJE
        FROM dbo.LOT_ORDENSEGUI 
        WHERE dbo.LOT_ORDENSEGUI.OCANUMERO = DATA_CODIGO.OCANUMERO AND dbo.LOT_ORDENSEGUI.OSEGCODIGO = '0004'
) AS criterio_4 ,

(
        SELECT TOP 1 dbo.LOT_ORDENSEGUI.OSEGPUNTAJE
        FROM dbo.LOT_ORDENSEGUI 
        WHERE dbo.LOT_ORDENSEGUI.OCANUMERO = DATA_CODIGO.OCANUMERO AND dbo.LOT_ORDENSEGUI.OSEGCODIGO = '0005'
) AS criterio_5 ,

(
        SELECT TOP 1 dbo.LOT_ORDENSEGUI.OSEGPUNTAJE
        FROM dbo.LOT_ORDENSEGUI 
        WHERE dbo.LOT_ORDENSEGUI.OCANUMERO = DATA_CODIGO.OCANUMERO AND dbo.LOT_ORDENSEGUI.OSEGCODIGO = '0006'
) AS criterio_6 ,

(
        SELECT TOP 1 dbo.LOT_ORDENSEGUI.OSEGPUNTAJE
        FROM dbo.LOT_ORDENSEGUI 
        WHERE dbo.LOT_ORDENSEGUI.OCANUMERO = DATA_CODIGO.OCANUMERO AND dbo.LOT_ORDENSEGUI.OSEGCODIGO = '0007'
) AS criterio_7

FROM (SELECT DISTINCT dbo.LOT_ORDENSEGUI.OCANUMERO 
FROM
dbo.LOT_ORDENSEGUI 
WHERE dbo.LOT_ORDENSEGUI.OCAANOORD = VARIABLE_AÑO
GROUP BY dbo.LOT_ORDENSEGUI.OCANUMERO ) AS DATA_CODIGO
```

### 3. Estructura del reporte

Enlace de la cabecera del reporte de proveedores

https://docs.google.com/spreadsheets/d/1i4x2B7q1UwLLbyjbQOFesqdUN9p4T4qGZhMJ7r8scEg/edit?usp=sharing

Criterios de evaluacion 

1. Cumplio con las especificaciones técnicas y de funcionalidad requeridas de acuerdo a la orden de compra/servicio/contrato.(25 puntos)
2. Los productos entregados estaban en buenas condiciones fìsicas y su apariencia satisface las expectativas ofrecidas a SERPETBOL (25 puntos)
3. La entrega se realizo en los tiempos pactados en la óden de compra/servicio/contrato.(15 puntos)
4. La mercancía y/o servicio suministrada por el Proveedor llega en su totalidad, correctamente empacada y sin daños, roturas o faltantes.(15 puntos)
5. No se generaron gastos adicionales, cumplió con las garantías ofrecidas, brindó el transporte del bien/servicio, etc.(5 puntos)
6. El Proveedor o Contratista suministra soporte de Post y Pre-venta, ademas de información del uso del producto y/o servicio.(5 puntos)
7. Volvería a contratar los servicios del Proveedor o Contratista en una futura adquisición.(10 puntos)



