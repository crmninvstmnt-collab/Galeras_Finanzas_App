# Control Financiero - Flutter / Android

Proyecto fuente inicial de una aplicación local. Importa los 14 registros de cartera del Excel vigente y los 31 artículos identificados en el catálogo de platería y belleza.

## Módulos incluidos
- Resumen de activos COP y USD separados.
- Cartera: consulta de deudores, abonos y creación de préstamos.
- Inventario: catálogo, actualización de existencias y registro de ventas.
- Movimientos: ingresos y egresos.
- Deudas por pagar: creación de obligaciones y registro de abonos.

## Datos iniciales importados
- Caja: $4.400.000 COP.
- Divisas: USD 150, sin conversión.
- Cuenta por cobrar familiar: $11.405.000 COP.
- 14 clientes con capital/total pactado/cuota cuando esos datos estaban en el Excel.
- Catálogo de 31 productos desde `INVENTARIO CAMILO.xlsx`.

## Reglas conservadas
El Excel no define una tasa de interés global aplicable a todos los préstamos. Por eso se conservan los valores de capital y total pactado de cada cliente, sin inventar una tasa común.
La regla propuesta de multa es 25% diario después de las 4:00 p. m. sobre la cuota vencida. Queda desactivada: el propio archivo la deja pendiente de validación contractual y legal.

## Inventario
El archivo fuente no contiene cantidades disponibles. Los artículos se cargan con stock 0; registra las existencias físicas tocando cada producto antes de registrar ventas.

## Generar el APK
Necesitas un computador Windows, macOS o Linux. El teléfono Android por sí solo no es suficiente para compilar cómodamente este proyecto.

1. Instala Flutter SDK y Android Studio.
2. Descomprime el ZIP.
3. Abre una terminal dentro de la carpeta `Galeras_Finanzas_App`.
4. Ejecuta estos comandos, en este orden:
   ```bash
   flutter create --platforms=android .
   flutter pub get
   flutter doctor
   flutter run
   ```
5. Para generar el APK:
   ```bash
   flutter build apk --release
   ```
6. El archivo se crea en:
   `build/app/outputs/flutter-apk/app-release.apk`

## Alcance y precauciones
Esta es una primera versión funcional del código, no una contabilidad auditada ni un APK ya compilado. En este entorno no está instalado Flutter/Android SDK para compilar y probar el APK.
La base de datos SQLite queda local en el teléfono. Antes de operar con dinero real, conviene implementar exportación/restauración de copias de seguridad, calendario detallado de cuotas, cálculo de mora sujeto a validación, edición de tasas/condiciones y conciliación inicial de saldos. No desinstales la app luego de ingresar datos sin respaldar su base local.
