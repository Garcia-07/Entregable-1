# Reporte de Minería de Datos

**Proyecto:** ObraTech
**Fecha:** 13/10/2026

## 1. Definición del problema

ObraTech es una plataforma orientada a conectar clientes, constructoras, contratistas y trabajadores de la construcción en Colombia   . El proyecto busca analizar patrones en los contratos públicos (usando datos del SECOP II) para evaluar cómo los atributos registrados se relacionan con el estado contractual actual, apoyando la toma de decisiones y la gestión de proyectos   .

- **Tipo de tarea:** clasificacion
- **Variable objetivo:** Estado Contrato

## 2. Datos

- **Archivo:** CCE_secop_ii_20261013.csv
- **Filas:** 4400
- **Columnas:** 67
- **Numéricas:** Documento Proveedor, Saldo Vigencia, Dias adicionados, Recursos Propios (Alcaldías, Gobernaciones y Resguardos Indígenas), Codigo Proveedor
- **Categóricas:** Nombre Entidad, Nit Entidad, Departamento, Ciudad, Localización, Orden, Sector, Rama, Entidad Centralizada, Proceso de Compra, ID Contrato, Referencia del Contrato, Estado Contrato, Codigo de Categoria Principal, Descripcion del Proceso, Tipo de Contrato, Modalidad de Contratacion, Justificacion Modalidad de Contratacion, Fecha de Firma, Fecha de Inicio del Contrato, Fecha de Fin del Contrato, Condiciones de Entrega, TipoDocProveedor, Proveedor Adjudicado, Es Grupo, Es Pyme, Habilita Pago Adelantado, Liquidación, Obligación Ambiental, Obligaciones Postconsumo, Reversion, Origen de los Recursos, Destino Gasto, Valor del Contrato, Valor de pago adelantado, Valor Facturado, Valor Pendiente de Pago, Valor Pagado, Valor Amortizado, Valor Pendiente de Amortizacion, Valor Pendiente de Ejecucion, Saldo CDP, EsPostConflicto, Puntos del Acuerdo, Pilares del Acuerdo, URLProceso, Nombre Representante Legal, Nacionalidad Representante Legal, Domicilio Representante Legal, Tipo de Identificación Representante Legal, Identificación Representante Legal, Género Representante Legal, Presupuesto General de la Nacion – PGN, Sistema General de Participaciones, Sistema General de Regalías, Recursos de Credito, Recursos Propios, Ultima Actualizacion, Codigo Entidad, Fecha Inicio Liquidacion, Fecha Fin Liquidacion, Objeto del Contrato

## 3. Preprocesamiento

- **Nulos:** median
- **Outliers:** winsorize
- **Escalado:** standard
- **Codificación:** onehot

## 4. Modelado

- **Algoritmo:** Random Forest
- **Test size:** 0.2
- **Random state:** 42

## 5. Evaluación

Métricas sugeridas para clasificacion:

- **Accuracy** (accuracy_score): Proporción de aciertos globales.
- **Precision** (precision_score): De los predichos positivos, cuántos lo son realmente.
- **Recall** (recall_score): De los positivos reales, cuántos se detectaron.
- **F1-Score** (f1_score): Media armónica entre Precision y Recall.
- **Matriz de confusión** (confusion_matrix): Tabla VP, VN, FP, FN.

---
*Generado por la Guía Interactiva de Minería de Datos*