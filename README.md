# GS Calidad Técnica ESPT

PWA offline para inspección de calidad técnica (Información OS, Medidor, Celda, Ducto 1", Acometida, SPT).
Desarrollado por Heidi Díaz.

## Uso
1. Menú ⋮ → *Cargar pendientes del día* (CSV/JSON de Inspecciones_Pendientes_ESPT).
2. Inspeccionar (por defecto solo las órdenes del supervisor; «ver todas» para el resto).
3. Pestaña *Enviar* → genera `Supervisor_Fecha.zip` (`inspecciones.json` + `fotos/`) y se sube a SharePoint (`Entrada_Inspecciones`).

## Esquema `GS_Calidad_Tecnica_ESPT_v1`
Por inspección: IdInspeccion (`orden_supervisor`), Title, Fecha_Inspeccion, Supervisor, Supervisor_asignado,
Hallazgos_/Estado_ de infor_OS, Medidor, Celda, Ducto, Acometida, SPT (hallazgos unidos con " / "),
Resultado_inspeccion, Observaciones_inspeccion, Direccion, Medidor_Instalado, Localidad, Fotos[], Hallazgos_detalle[].
Las claves `*_Ducto` van sin comillas: el flujo las mapea a `Hallazgos_Ducto 1"` / `Estado_Ducto 1"`.

## Reglas
Llave orden+supervisor (no se repite por supervisor; dos supervisores sí pueden registrar la misma orden → flujo marca `Orden_repetida`).
Lo exportado queda bloqueado (se puede reabrir con confirmación).
